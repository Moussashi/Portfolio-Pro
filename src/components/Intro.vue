<template>
    <div id="appCanvas">
      <div id="title">
        <h1>
          Welcome
        </h1>

        <router-link to="/portfolio/home">
            <button class="myButton">Enter</button>
        </router-link>
      </div>
    </div>
</template>

<script>
import * as THREE from 'three';
import * as dat from 'dat.gui';
import gsap from 'gsap'
const OrbitControls = require('three-orbitcontrols')
const gui = new dat.GUI();

export default {
    data() {
        return {
            canvas: true
        }
    },
    methods: {
        createCanvas() {
                        // GUI
            //gui hidden
            dat.GUI.toggleHide();
            const world = {
                plane: {
                    width: 400,
                    height: 400,
                    widthSegments: 50,
                    heightSegments: 50,
                }
            }

            //gui.add(world.plane, 'width', 1, 500).onChange(generatePlane)
            //gui.add(world.plane, 'height', 1, 500).onChange(generatePlane)
            //gui.add(world.plane, 'widthSegments', 1, 100).onChange(generatePlane)
            //gui.add(world.plane, 'heightSegments', 1, 100).onChange(generatePlane)
            console.log(gui);

            function generatePlane() {
                planeMesh.geometry.dispose()
                planeMesh.geometry = new THREE.PlaneGeometry(
                    world.plane.width,
                    world.plane.height,
                    world.plane.widthSegments,
                    world.plane.heightSegments
                )

                //      VERTICE POSITION RANDOMIZATION


                const { array } = planeMesh.geometry.attributes.position
                const randomValues = []
                for (let i = 0; i < array.length; i++) {

                    if (i % 3 === 0 ){
                        const x = array[i]
                        const y = array[i + 1]
                        const z = array[i + 2]

                        array[i] = x + (Math.random() - 0.5) * 3
                        array[i + 1] = y + (Math.random() - 0.5) * 3
                        array[i + 2] = z + (Math.random() - 0.5) * 7
                    }

                    randomValues.push(Math.random()  * Math.PI * 2)
                }

                planeMesh.geometry.attributes.position.randomValues = randomValues //add new property (randomValues)
                planeMesh.geometry.attributes.position.originalPosition = planeMesh.geometry.attributes.position.array //add new property (originalPosition)

                const colors = []
                for (let i = 0; i < planeMesh.geometry.attributes.position.count; i++) {
                    colors.push(1, 1, 1)
                }

            planeMesh.geometry.setAttribute('color', new THREE.BufferAttribute(
                new Float32Array(colors), 3)
            )
            }


            //    $$$$$$$$$$$$$$$  CAMERA  $$$$$$$$$$$$$$$$$$$$$$ 


            const raycaster = new THREE.Raycaster() //kind of a laser pointer
            const camera = new THREE.PerspectiveCamera(
                    75, 
                    window.innerWidth / window.innerHeight,
                    0.01,
                    1000)
            const scene = new THREE.Scene();
            const renderer = new THREE.WebGL1Renderer( { antialias: true } ) //canvas

            renderer.setSize(innerWidth, innerHeight) //size of the Canvas
            renderer.setPixelRatio(devicePixelRatio)

            const app = document.getElementById('appCanvas')
            app.appendChild(renderer.domElement) // add the canvas to the dom

            new OrbitControls(camera, renderer.domElement)
            camera.position.z = 50



            //    $$$$$$$$   PLANE   $$$$$$$$$$$$$$$$$$

            const planeGeometry = new THREE.
                PlaneGeometry(
                    world.plane.width, 
                    world.plane.height,
                    world.plane.widthSegments,
                    world.plane.heightSegments
                    )

            const PlaneMaterial = new THREE.MeshPhongMaterial({
                side: THREE.DoubleSide,
                flatShading: THREE.FlatShading,
                vertexColors: true
            })
            const planeMesh = new THREE.Mesh(planeGeometry, PlaneMaterial)

            scene.add(planeMesh)
            generatePlane()



            // $$$$$$$$$$$$$$$$$$$$$ LIGHTS $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$


            const light = new THREE.DirectionalLight(
                0xffffff, 1
            )
            light.position.set(0, -1, 1)
            scene.add(light)

            const backLight = new THREE.DirectionalLight(
                0xffffff, 1
            )
            backLight.position.set(0, 0, -1)
            scene.add(backLight)

            const mouse = {
                x: undefined,
                y : undefined
            }


            //                  $$$$$$  ANIMATE  $$$$$$

            let frame = 0
            function animate() {
                requestAnimationFrame(animate)
                frame += 0.01
                renderer.render(scene, camera)
                raycaster.setFromCamera(mouse, camera)
                
                const { array, originalPosition, randomValues } = planeMesh.geometry.attributes.position

                for (let i = 0; i < array.length; i += 3) {

                    //x
                    array[i] = originalPosition[i] + Math.cos(frame + randomValues[i]) * 0.01
                    //y
                    array[i + 1] = originalPosition[i + 1] + Math.cos(frame + randomValues[i + 1]) * 0.01
                    //z
                }

                planeMesh.geometry.attributes.position.needsUpdate = true

                const intersects = raycaster.intersectObject(planeMesh)

                if (intersects.length > 0) {

                        const { color } = intersects[0].object.geometry.attributes
                        
                        //vertice 1
                        color.setX(intersects[0].face.a, 0.0)  //vertices to change colors
                        color.setY(intersects[0].face.a, 1)
                        color.setZ(intersects[0].face.a, 0.0)

                        //vertice 2
                        color.setX(intersects[0].face.b, 0.0)  //vertices to change colors
                        color.setY(intersects[0].face.b, 1)
                        color.setZ(intersects[0].face.b, 0.0)

                        //vertice 3
                        color.setX(intersects[0].face.c, 0.0)  //vertices to change colors
                        color.setY(intersects[0].face.c, 1)
                        color.setZ(intersects[0].face.c, 0.0)

                        

                    intersects[0].object.geometry.attributes.color.needsUpdate = true

                    const initialColor = {
                        r: 1,
                        g: 1,
                        b: 1
                    }
                    const hoverColor = {
                        r: 0.1,
                        g: 0.1,
                        b: 0.1
                    }
                    gsap.to(hoverColor, {
                        r: initialColor.r,
                        g: initialColor.g,
                        b: initialColor.b,
                        onUpdate: () => {
                            color.setX(intersects[0].face.a, hoverColor.r)  //vertices to change colors
                            color.setY(intersects[0].face.a, hoverColor.g)
                            color.setZ(intersects[0].face.a, hoverColor.b)
                    
                            //vertice 2
                            color.setX(intersects[0].face.b, hoverColor.r)  //vertices to change colors
                            color.setY(intersects[0].face.b, hoverColor.g)
                            color.setZ(intersects[0].face.b, hoverColor.b)
                    
                            //vertice 3
                            color.setX(intersects[0].face.c, hoverColor.r)  //vertices to change colors
                            color.setY(intersects[0].face.c, hoverColor.g)
                            color.setZ(intersects[0].face.c, hoverColor.b)
                            color.needsUpdate = true
                        }
                    })
                }
            

            }

            //renderer.render(scene, camera)
                animate()
            


            // MOUSE moving the canvas

            addEventListener('mousemove', (event) => {
                mouse.x = (event.clientX / innerWidth) * 2 - 1  //  1 to the right    -1 to the left
                mouse.y = -(event.clientY / innerHeight) * 2 + 1
            
            })

        }
    },
    mounted() {
        if (this.$router.currentRoute._rawValue.fullPath === '/portfolio/') {
            return this.createCanvas()
        }
    }
}
</script>

<style scoped>
@font-face {
    font-family: 'Audrey';
    src: url('../assets/Audrey-Normal.otf');
}
@font-face {
    font-family: 'Monoton';
    src: url('../assets/Monoton-Regular.ttf');
}

html, body {
  padding: 0;
  margin: 0;
}
#appCanvas {
  font-family: Monoton, 'Times New Roman', Times, serif, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}
#title {
  color: rgb(19, 19, 19);
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 2rem;
  text-align: center;
}
.myButton {
	box-shadow: 3px 4px 0px 0px #899599;
	background:linear-gradient(to bottom, #ededed 5%, #bab1ba 100%);
	background-color:#ededed;
	border-radius:15px;
	border:1px solid #d6bcd6;
	display:inline-block;
	cursor:pointer;
	color:#3a8a9e;
	font-family: Audrey;
	font-size:1.3rem;
	padding:3% 15%;
	text-decoration:none;
	text-shadow:0px 1px 0px #e1e2ed;
}
.myButton:hover {
	background:linear-gradient(to bottom, #bab1ba 5%, #ededed 100%);
	background-color:#bab1ba;
}
.myButton:active {
	position:relative;
	top:1px;
}
h1 {
    font-size: 5rem;
    color: #3a8a9e;
}

</style>