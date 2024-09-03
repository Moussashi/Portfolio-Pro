<template>
  <div id="wrapper">
    <div id="presentation">

      <!--VIDEO BACKGROUND-->

      <div class="video-wrapper">
        <video playsinline autoplay muted loop>
          <source src="../assets/smokeW.mp4" type="video/mp4" poster="..assets/fallback.png">
          <source src="../assets/smokeW.webm" type="video/webm" poster="..assets/fallback.png">
          Your browser does not support the video tag.
        </video>
        <div class="header">
          <h3 id="title"> {{ title }} </h3>
          <h4 id="title2"> {{ title2 }} </h4>
          <h1 id="name"> {{ name }} </h1>
        </div>


        <nav>
          <div class="navigation">
            <button v-if="!navDeployed" :class="leave" id="triforce" @click="toggleButton()">Navigate</button>
            <button v-else id="navDeployed" @click="toggleButton()">Hide</button>
            
            <transition name="fade">
            <div class="components" v-if="navDeployed">
              <router-link to="/portfolio/work" :class="disapear"> <p>Work</p> </router-link>
              <router-link to="/portfolio/resume"> <p>Resume</p> </router-link>
              <router-link to="/portfolio/contact"> <p>Contact</p> </router-link>
            </div>
            </transition>

          </div>
        </nav>

      </div>

    </div>


  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Welcome",
      title: "I'm Moussa Sy -  Web Analyst",
      title2: "Based in Paris, France",
      navDeployed: false,
      leave: null,
      disapear: null
    }
  },
  methods: {
    toggleButton() {
      this.navDeployed = !this.navDeployed

      if (!this.navDeployed) {
        this.leave = 'leave'
      } else {
        this.leave = null
      }

    }
  }
}
</script>

<style scoped>
/********************************************
******************** FONTS ******************
*********************************************/
@font-face {
    font-family: 'Monoton';
    src: url('../assets/Monoton-Regular.ttf');
}
@font-face {
    font-family: 'Audrey';
    src: url('../assets/Audrey-Normal.otf');
}
/********************************************
******************** GENERAL ******************
*********************************************/
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 5%;
  font-family: 'Courier New', Courier, monospace;
}
#wrapper {
  height: 100vh;
}
#name {
  color: black;
  font-size: 3em;
  text-align: center;
  margin-bottom: 0;
  animation: arrival 3s forwards;
  font-family: Monoton;
}
#title {
  color: black;
  font-size: 1.8rem;
  text-align: center;
  margin-top: 0;
  animation: arrival 4s forwards;
}
#title2 {
  color: black;
  animation: arrival 4s forwards;
  text-align: center;
  font-size: 1.8rem;
}
#presentation {
  border: #2c3e50 solid 1px;
  width: 100vw;
  height: 30vh;
}
header {
  position: relative;
}
.navigation {
  width: 50vw;
  height: 40vh;
  margin: auto;
  display: flex;
  flex-direction: column;
  text-align: center;
}
.components {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  animation: arrivalY 1.2s forwards;
  padding: 1%;
  margin-top: 10%;
  width: auto;
}
.components p {
  font-size: 2rem;
}
button {
  z-index: 2;
  padding: 3%;
  font-family: Audrey;
  font-size: 1.5rem;
}
a {
  color: black;
  text-decoration: none;
  font-size: 3rem;
}
p {
  font-size: 45%;
  color: black;
}
p:hover {
  animation: underline 1s forwards;
  color: black;
}
#triforce {
  width: 25vw;
  margin: 0 auto;
  text-align: center;
  font-size: 2rem;
}
#navDeployed {
  width: 20vw;
  margin: 0 auto;
  font-size: 2rem;
}
/********************************************
******************** VIDEO ******************
*********************************************/
video {
  object-fit: cover;
  height: 100%;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
}
.video-wrapper {
  /* Telling our absolute positioned video to 
  be relative to this element */
  position: relative;

  width: 100vw;
  height: 100vh;

  /* Will not allow the video to overflow the 
  container */
  overflow: hidden;

  /* Centering the container's content vertically 
  and horizontally */
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
}

/********************************************
*************** ANIMATIONS ******************
*********************************************/


.fade-enter-active, .fade-leave-active {
  animation: arrivalY 2s forwards;
}
.fade-enter, .fade-leave-to {
  animation: leaveY 2s forwards;
}

@keyframes arrival {
  from {
    opacity: 0.5;
  }
  to {
    opacity: 1;
  }
}
@keyframes arrivalY {
  from {
    transform: translateY(-250px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}
@keyframes leaveY {
  from {
    transform: translateY(0);
    opacity: 1;
  }
    to {
      transform: translateY(-150px);
      opacity: 0;
    }
}
@keyframes underline {
  from {
    text-decoration: none;
  }
  to {
    text-decoration: underline goldenrod 2px;
    background-color: rgb(239, 228, 221);
    padding: 10%;
  }
}

/********************************************
*************** RESPONSIVE ******************
*********************************************/

@media only screen and (max-width: 450px) {
  button {
    font-size: 1rem;
  }
  .components {
    flex-direction: column;
  }
}
</style>