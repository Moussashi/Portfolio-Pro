<template>

    <div id="languageBtn">
        <button @click="toggleLang"> {{ language }} </button>
    </div>
    
    <div id="wrapper">
        
        <!-- Title -->
        <section id="Title">
            <ul>
                <li 
                    v-for="tl in title" 
                    :key="tl"
                    class="letters"
                    >
                    <h1> {{ tl }} </h1>
                </li>
            </ul>  

            <!-- Navigation Bar -->
            <nav-bar 
                id="nav"
                :home="navbar.home"
                :resume="navbar.resume"
                :contact="navbar.contact"></nav-bar>

        </section>

        <!-- How i work -->
        <h1 v-if="english">My Projects</h1>
        <h1 v-else>Mes projets</h1>
        <section>
            <div class="projects">
                <div class="prjTxt">
                    <h2>Machine learning project</h2>
                    <h4 v-if="english">Small Ml project, the goal was to create a model which could differenciate real and false bill</h4>
                    <h4 v-else>Projet d'introduction au Machine learning, le but étant de créer un model pouvant différencier vrais et faux billets</h4>
                    <button class="btn1">Voir ce projet</button>
                </div>
                <div class="prjImg">
                    <img src="../assets/machine.jpeg" alt="">
                </div>
            </div>

            <div class="separator"><fa class="icon" icon="cloud"/></div>

            <div class="projects">
                <div class="prjImg">
                    <img src="../assets/map.png" alt="">
                </div>
                <div class="prjTxt">
                    <h2>Visualisations</h2>
                    <h4 v-if="english">Different visualisation created for projects or fun</h4>
                    <h4 v-else>Differentes visualisations crées pour des projects ou pour le plaisir </h4>
                    <button v-if="english" class="btn2"><a href="https://public.tableau.com/app/profile/moussa.sy/vizzes" target="blank_"></a>Check projects</button>
                    <button v-else class="btn2"><a href="https://public.tableau.com/app/profile/moussa.sy/vizzes"></a>voir ces projets</button>
                </div>
            </div>

            <div class="separator"><fa class="icon" icon="cloud"/></div>

            <div class="projects">
                <div class="prjTxt">
                    <h2>MyFitPage</h2>
                    <h4>Projet en construction</h4>
                    <button class="btn3">-- <fa class="icon" icon="hammer"/>--</button>
                </div>
                <div class="prjImg">
                    <img src="../assets/comingSoon.png" alt="">
                </div>
            </div>
            
        </section>
        
    </div>
</template>


<script>
import navBar from './UI/navBar.vue'
export default {
    components: {
        navBar
    },
    data() {
        return {
            english: true,
            language: 'Fr',
            title: ['W', 'O', 'R', 'K'],
            french: true,
            navbar: {
                home: 'Home',
                work: 'Work',
                resume: 'Resume',
                contact: 'Contact'
            }
        }
    },
    methods: {
        toggleLang() {
            this.english = !this.english

            if (this.english) {
                this.language = 'En'
            } else {
                this.language = 'Fr'
            }
        }
    }
}
</script>


<style scoped>
/*********************************************
*********************FONTS********************
**********************************************/
@font-face {
    font-family: 'Monoton';
    src: url('../assets/Monoton-Regular.ttf');
}
@font-face {
    font-family: 'Audrey';
    src: url('../assets/Audrey-Normal.otf');
}




/*********************************************
****************GENERAL********************
**********************************************/

#languageBtn button {
background-color: white;
border-radius: 50%;
padding: 1%;
position: fixed;
z-index: 99;
top: 1%;
right: 1%;
}

#wrapper {
    width: 100vw;
    animation: pageUp 1.5s forwards;
    background: rgb(239,228,221);
    background: linear-gradient(90deg, rgba(239,228,221,1) 43%, rgba(255,255,255,1) 88%);
}
#Title {
    width: 100%;
    text-align: center;
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin: 0 auto;
    font-family: Monoton;
    font-size: 4vw;
    padding: 0;
}
#Title ul {
    margin: 0;
}
h1 {
    text-align: center;
    margin-bottom: 10%;
}
ul {
    display: flex;
    flex-direction: row;
    padding: 0;
}
li {
    list-style: none;
}
#nav {
    font-size: 2vw;
}
.letters:hover {
    animation: letters 0.5s ease-in-out
}
.projects {
    font-family: Audrey;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}
img {
    width: 80%;
}
.prjTxt, .prjImg {
    width: 50%;
    margin-bottom: 20%;
}
.btn1 {
  background: #FF4742;
  border: 1px solid #FF4742;
  border-radius: 6px;
  box-shadow: rgba(0, 0, 0, 0.1) 1px 2px 4px;
  box-sizing: border-box;
  color: #FFFFFF;
  cursor: pointer;
  display: inline-block;
  outline: 0;
  padding: 3% 6%;
  text-align: center;
  text-rendering: geometricprecision;
  text-transform: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
}

.btn1:hover,
.btn1:active {
  background-color: initial;
  background-position: 0 0;
  color: #FF4742;
}

.btn1:active {
  opacity: .5;
}
.btn2 {
  background-image: linear-gradient(92.88deg, #455EB5 9.16%, #5643CC 43.89%, #673FD7 64.72%);
  border-radius: 9px;
  border-style: none;
  box-sizing: border-box;
  color: #FFFFFF;
  padding: 3% 6%;
  cursor: pointer;
  text-align: center;
  text-shadow: rgba(0, 0, 0, 0.25) 0 3px 8px;
  transition: all .5s;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  height: 2%;
}

.btn2:hover {
  box-shadow: rgba(80, 63, 205, 0.5) 0 1px 30px;
  transition-duration: .1s;
}
.btn3 {
  background-image: linear-gradient(92.88deg, #575758 9.16%, #2a2a2a 43.89%, #1b191e 64.72%);
  border-radius: 8px;
  border-style: none;
  box-sizing: border-box;
  color: #FFFFFF;
  padding: 3% 6%;
  cursor: pointer;
  text-align: center;
  text-shadow: rgba(0, 0, 0, 0.25) 0 3px 8px;
  transition: all .5s;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  height: 2%;
}
.btn3:hover {
  box-shadow: rgba(4, 3, 9, 0.5) 0 1px 30px;
  transition-duration: .1s;
}
.icon {
    font-size: 1.5rem;
}
.separator {
  font-family: "Share Tech Mono", monospace;
  color: #fff;
  font-size: 6vh;
  text-shadow: 1px 1px 1px rgba(0, 0, 0, .45);
  margin-bottom: 20%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.separator::before,
  .separator::after {
    content: '';
    display: block;
    height: 0.09em;
    min-width: 30vw;
  }
  
  .separator::before {
    background: linear-gradient(to right, rgba(240,240,240,0), #fff);
    margin-right: 4vh;
  }
  
  .separator::after {
    background: linear-gradient(to left, rgba(240,240,240,0), #fff);
    margin-left: 4vh;
  } 

  .changeLanguage {
    animation: changeLanguage 1s forwards;
}

/*********************************************
****************ANIMATIONS********************
**********************************************/

@keyframes pageUp {
    from {
        transform: translateY(100vh);
    }
    to {
        transform: translateY(0);
    }
}
@keyframes letters {
    from {
        transform: translateY(0);
    }
    to {
        transform: translateY(-1vh);
        color: rgb(31, 29, 29);
    }
}

@keyframes changeLanguage {
    from {
        opacity: 0;
        transform: translateX(-50px);
    }
    to {
        opacity: 1;
        transform: translateX(0px);
    }
}

/*********************************************
************RESPONSIVE************************
**********************************************/
@media only screen and (max-width: 769px) {
    #Title {
        flex-direction: column;
        justify-content: center;
        padding: 0;
        border: 0;
    }
}
</style>
