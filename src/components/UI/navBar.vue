<template>
    <nav>
        <fa class="icon" icon="bars" v-if="!drop" @click="dropMenu()"/>
        <fa class="icon" icon="x" v-else @click="dropMenu()"/>
        <div v-if="drop" id="droplist">

            <transition
                appear
                @enter="navAppear"
            >
            <ul>
                <router-link to="/portfolio/home"> {{ home }} </router-link>
                <router-link to="/portfolio/work"> {{ work }} </router-link>
                <router-link to="/portfolio/resume"> {{ resume }} </router-link>
                <router-link to="/portfolio/contact"> {{ contact }} </router-link>
            </ul>
        </transition>
        </div>

    </nav>
</template>

<script>
import gsap from 'gsap'
export default {
    props: {
        home: {
            required: false,
            type: String
        },
        work: {
            required: false,
            type: String
        },
        resume: {
            required: false,
            type: String
        },
        contact: {
            required: false,
            type: String
        },
    },
    data() {
        const navAppear = (el) => {
            gsap.from(el, {
                duration: 1,
                y: -100,
                opacity: 0,
                ease: 'power2'
            })
        }
        return {
            drop: false,
            navAppear,
        }
    },
    methods: {
        dropMenu() {
            this.drop = !this.drop
        }
    }
}
</script>

<style scoped>
nav {
    width: 10vw;
    text-align: center;
}
#droplist {
    text-align: center;
}
ul {
    padding: 0;
    height: 15vh;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: white;
}
li {
    list-style: none;
    color: black;
}
a {
    font-size: 1.5rem;
}
a:visited {
    color: black;
}
a:hover {
    background-color: white;
    padding: 1%;
}
.icon {
    background-color: white;
    font-size: 3vw;
    border-radius: 50%;
    padding: 1%;
    animation: icon 0.7s forwards;
}
.icon:hover {
    background-color: black;
    color: white;
}

@keyframes icon {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

@media only screen and (max-width: 769px) {
    .icon {
        font-size: 5vw;
    }
}
</style>