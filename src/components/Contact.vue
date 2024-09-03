<template>
  <div id="wrapper">
    <div id="Title">
      <ul>
        <li v-for="tl in title" :key="tl" class="letters">
          <h1>{{ tl }}</h1>
        </li>
      </ul>
      <nav-bar
        id="nav"
        :home="navbar.home"
        :resume="navbar.resume"
        :work="navbar.work"
      >
      </nav-bar>
    </div>

    <section id="contact">
      <Form
        action="https://formsubmit.co/4c4c1af5e6570c4d4520dbc52ce9bde2"
        method="POST"
      >
        <label for="Name">Your Name</label>
        <input type="text" name="name" required />

        <label for="Name">Email Adress</label>
        <input type="email" name="email" required />

        <label for="message">Message</label>
        <textarea
          type="text"
          name="message"
          cols="60"
          rows="8"
          placeholder="Insert your message here"
          required
        ></textarea>

        <button type="submit" @click="submitMail">Let's Talk</button>
      </Form>

      <!-- THE LEAFLET MAP -->

      <custom-map id="map"></custom-map>
    </section>
    <p v-if="thanks">{{ message }}</p>
  </div>
</template>

<script>
import CustomMap from "./Map.vue";
import navBar from "./UI/navBar.vue";
export default {
  components: { CustomMap, navBar },
  data() {
    return {
      title: ["C", "O", "N", "T", "A", "C", "T"],
      navbar: {
        home: "Home",
        work: "Work",
        resume: "Resume",
        contact: "Contact",
        thanks: false,
        message: "Thank you, I will respond as soon as possible",
      },
    };
  },
  methods: {
    submitMail() {
      this.thanks = true;

      const redirect = () => {
        this.$router.push("/portfolio/home");
      };

      setTimeout(redirect, 1000);
    },
  },
};
</script>

<style scoped>
#page {
  display: flex;
}
#banniere {
  border: solid 1px red;
  width: 100px;
  height: 500px;
}
#cv {
  border: solid 1px blue;
  width: 100%;
  height: 500px;
}
#main {
  display: flex;
}
.para {
  color: blueviolet;
  border: solid white 2px;
}
/*********************************************
*********************FONTS********************
**********************************************/

@font-face {
  font-family: "Monoton";
  src: url("../assets/Monoton-Regular.ttf");
}

/*********************************************
*******************GENERAL********************
**********************************************/
#wrapper {
  width: 100vw;
  height: 100vh;
  background: rgb(239, 228, 221);
  background: linear-gradient(
    90deg,
    rgba(239, 228, 221, 1) 43%,
    rgba(255, 255, 255, 1) 88%
  );
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  animation: pageDown 2s forwards;
}
#Title {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
  font-family: Monoton;
  color: black;
}
h1 {
  font-size: 3em;
  text-align: center;
  margin-bottom: 0;
}

form {
  display: flex;
  flex-direction: column;
  width: 50%;
  padding: 1%;
}
button {
  background-color: rgb(239, 228, 221);
  border: none;
  padding: 5%;
  border-top: 5px;
  width: 50%;
  align-self: center;
}
button:hover {
  animation: buttonHov 0.3s forwards;
}

#contact {
  display: flex;
  justify-content: space-between;
  height: 50vh;
}
form {
  width: 30%;
}
img {
  animation: mapOut 0.3s forwards;
}
img:hover {
  animation: mapGrow 0.3s forwards;
}
#map {
  width: 60%;
}
ul {
  display: flex;
  font-size: 2rem;
  padding: 0;
}
.letters {
  list-style: none;
}
.letters:hover {
  animation: letters 0.5s ease-in-out;
}

/*********************************************
****************ANIMATIONS********************
**********************************************/
@keyframes pageDown {
  from {
    transform: translateY(-100vh);
  }
  to {
    transform: translateY(0);
  }
}
@keyframes buttonHov {
  100% {
    width: 100%;
    background-color: black;
    color: rgb(239, 228, 221);
    font-weight: bolder;
    font-size: larger;
  }
}
@keyframes mapGrow {
  from {
    width: 40%;
  }
  to {
    width: 55%;
  }
}
@keyframes mapOut {
  from {
    width: 55%;
  }
  to {
    width: 40%;
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
/*********************************
**********RESPONSIVE**************
**********************************/
@media only screen and (max-width: 769px) {
  #Title {
    display: flex;
    flex-direction: column;
  }
  #contact {
    display: flex;
    width: 100vw;
    height: 70vh;
    flex-direction: column;
    align-items: center;
  }
  #map {
    width: 80%;
    height: 50vh;
    border: black 1px solid;
  }
  form {
    width: 70%;
  }
  #nav {
    font-size: 1.5rem;
  }
  h1 {
    font-size: 3rem;
    margin: auto;
  }
}
</style>