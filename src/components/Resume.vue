<template>
    
    <div id="languageBtn">
        <button @click="toggleLang"> {{ language }} </button>
    </div>
    <div class="wrapper">

        <div class="title_wrapper">

            <div class="title_description">
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

                <nav-bar 
                    id="nav"
                    :home="navbar.home"
                    :work="navbar.work"
                    :contact="navbar.contact"></nav-bar>

                </section>

                <section id="description"> 
                    
                <div v-if="!english" class="changeLanguage">
                    <img src="../assets/plume.png" alt="plume en ecriture">
                    
                    <p>

                            Fort d'un parcours en développement web et animé par une passion pour les données, je suis entré dans le monde de l'analyse de données, apportant une perspective unique.<br>
                            
                            Mes 2 années d'expérience en analyse web m'ont permis de combler le fossé entre les connaissances techniques et le comportement des utilisateurs, favorisant la compréhension de la façon dont les données se traduisent en actions concrètes.<br>

                            J'ai perfectionné mes compétences en programmation (y compris Python, SQL) au cours de mon parcours en data, construisant une base solide pour le nettoyage et l'analyse des données. <br>Cette expertise technique s'est avérée précieuse dans mon rôle d'analyste web, où j'ai utilisé divers outils et techniques pour extraire des informations exploitables des données de trafic de site Web et de comportement des utilisateurs.

                            L'identification des tendances, des modèles et des anomalies est devenue ma spécialité. Ces informations m'ont permis de collaborer avec les équipes et d'optimiser les performances du site Web, d'améliorer l'expérience utilisateur et, en fin de compte, d'atteindre les objectifs commerciaux. <br>Cependant, ma véritable passion est de transformer des données brutes en récits convaincants.

                            C'est là que mon expertise dans Tableau prend tout son sens. Je maîtrise la création de tableaux de bord, de graphiques et de rapports visuellement attrayants qui communiquent efficacement des histoires de données complexes à un public à la fois technique et non technique. <br> L'adaptation des visualisations aux besoins spécifiques de l'entreprise garantit que les informations trouvent un écho auprès des parties prenantes et éclairent les décisions basées sur les données.
                    </p>
                </div>

                <div v-else>
                    <img src="../assets/plume.png" class="quill" alt="plume en ecriture">
                    
                    <p class="changeLanguage">
                        With a background in web development and a passion for data, I transitioned into the world of data analysis, bringing a unique perspective to the table. <br> My 2 years of web analytics experience allowed me to bridge the gap between technical knowledge and user behavior, fostering an understanding of how data translates into real-world actions.

                        I honed my programming skills (including Python and SQL) during my data journey, building a strong foundation for data wrangling and analysis.<br> This technical expertise proved invaluable in my web analyst role, where I utilized various tools and techniques to extract meaningful insights from website traffic and user behavior data.<br>

                        Identifying trends, patterns, and anomalies became my specialty.<br> These insights empowered me to collaborate with teams and optimize website performance, enhance user experience, and ultimately drive business objectives. <br>However, my true passion lies in transforming data into compelling narratives.

                        This is where my expertise in Tableau shines. I excel at creating visually engaging dashboards, charts, and reports that effectively communicate complex data stories to both technical and non-technical audiences. <br>Tailoring visualizations to specific business needs ensures that insights resonate with stakeholders and inform data-driven decisions work ethic, a collaborative spirit, and a continuous hunger for learning. I am proficient in communicating complex data concepts into clear and concise language, ensuring everyone is on the same page.</p>
                </div>

            </section>
            </div>
            <img src="../assets/CVpro.jpg" class="CV" alt="CV pro">

        </div>

        <!-- RESUME -->


        <div id="resume">
            

                <section id="interests">
                    <h2>interests</h2>
                    <div id="galerie">

                        <!--SECTION CHESS AND ASTRONOMY-->
                        <div class="chess_astro">
                            <div class="galerieCard chess"> 
                                <h3>Chess <fa class="icon" icon="chess"/></h3>
                                <p v-if="!english" class="changeLanguage">Recente découverte devenue une passion par son coté stratégique</p>
                                
                                <p v-else class="changeLanguage">
                                    Recent discovery which became a passion through it's strategic aspect
                                </p>
                            </div>

                            <div class="galerieCard astro">
                                <h3>Astronomy <fa class="icon" icon="meteor"/></h3>
                                <p v-if="!english" class="changeLanguage">Passion pour l'astronomie depuis l'enfance 
                                    Un amour des paysages qui s'est étendu au-delà de l'exosphère</p>
                                
                                <p v-else class="changeLanguage">
                                    Passion for astronomy since childhood. A love for landscapes that went beyond the exosphere
                                </p>
                            </div>
                        </div>
                        
                        <div class="galerieCard bball">
                            
                            <div class="bballText books">
                                <h3>Lecture  <fa class="icon" icon="book-open"/></h3>
                                <p v-if="!english" class="changeLanguage">Amoureux de livres policiers et fantastiques, Dan Brown
                                    , Bernard Werber, Stephen King et tout particulièrement
                                     J.K Rowling et la série Harry Potter <fa class="icon" icon="bolt"/></p>

                                <p v-else class="changeLanguage">
                                    Love fantasy and detective novels, Dan Brown, Bernard Werber,
                                     Stephen King and especialy J.K Rowling with the harry potter 
                                     series <fa class="icon" icon="bolt"/>
                                </p>
                                
                            </div>

                            <div class="bballText">
                                <h3>Basket-Ball <fa class="icon" icon="basketball"/></h3>
                                <p v-if="!english" class="changeLanguage">Pratique active du basketball en compétition et pour le plaisir depuis 2003,
                                    suivi régulier de l'actualité basket et du sport en général (football, boxe, arts martiaux).
                                     Pratique d'art martiaux en club: boxe anglaise, Vo Vietnam, Hapkido, jiu jitsu brésilien
                                </p>
                                <p v-else class="changeLanguage">
                                    Played basketball in competition and as a hobby since 2003, follow sports actuality daily 
                                    (soccer, boxing, martial arts...). Martial artist (Boxing, Vo-Vietnam, Hapkido, brazilian Jiu jitsu)
                                </p>
                                <img src="../assets/bballMe.jpeg" alt="Photographie de moi même en activité">
                            </div>
                            
                        </div>
                    </div>
                </section>
                

        </div>
        
    </div>
    <div class="portraitTtl">
        <h2>Portrait Photography</h2>
    </div>

    <div aria-label="portrait photos" class="carousel" data-carousel>
        <button class="carousel-button prev" data-carousel-button="prev" >&#8666;</button>
        <button class="carousel-button next" data-carousel-button="next"  >&#8667;</button>
        <ul data-slides>
            <li class="slide" data-active>
                <img src="../assets/Kajal.jpg" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img10.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img2.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img6.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img11.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img1.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img35.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img36.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img17.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img38.png" alt="">
            </li>
            <li class="slide">
                <img src="../assets/img39.png" alt="">
            </li>
        </ul>
        
    </div>

</template>

<script>
import navBar from './UI/navBar.vue'
export default {
    components: {
        navBar,
    },
    data() {
        return {
            english: true,
            language: 'Fr',
            title: ['R', 'E', 'S', 'U', 'M', 'E'],
            navbar: {
                home: 'Home',
                work: 'Work',
                resume: 'Resume',
                contact: 'Contact',
            },
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
        },
        carousel() {
            const buttons = document.querySelectorAll("[data-carousel-button")
            buttons.forEach(button => {
                button.addEventListener("click", () => {
                    
                    const offset = button.dataset.carouselButton === "next" ? 1 : -1
                    const slides = button
                        .closest("[data-carousel]")
                        .querySelector("[data-slides]")
                    
                    const activeSlide = slides.querySelector("[data-active]")
                    let newIndex = [...slides.children].indexOf(activeSlide) + offset

                    if (newIndex < 0) newIndex = slides.children.length - 1
                    if (newIndex >= slides.children.length) newIndex = 0

                    slides.children[newIndex].dataset.active = true
                    delete activeSlide.dataset.active

                    
                })
            })
        }
    },
    mounted() {
        this.carousel()
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

/*********************************************
****************GENERAL********************
**********************************************/


.wrapper {
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100vw;
    animation: pageDown 2s forwards;
    background: rgb(239,228,221);
    background: linear-gradient(90deg, rgba(239,228,221,1) 43%, rgba(255,255,255,1) 88%);
}
.title_wrapper {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    padding-top: 10vh;
}
.title_description {
    display: flex;
    flex-direction: column;
    align-content: space-between;
    width: 90vw;
}
#resume {
    margin-top: 5vh;
    width: 70vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-size: 1.2rem;
}
#resume button {
    -webkit-box-shadow: 13px 12px 15px 5px rgba(92,92,92,0.58); 
    box-shadow: 13px 12px 15px 5px rgba(92,92,92,0.58);
}
#resume button:hover {
    -webkit-box-shadow: 5px 5px 15px 5px #FF8080, -9px 5px 15px 5px #FFE488, -7px -5px 15px 5px #8CFF85, 12px -5px 15px 5px #80C7FF, 12px 10px 15px 7px #E488FF, -10px 10px 15px 7px #FF616B, -10px -7px 27px 1px #8E5CFF, 13px 12px 15px 5px rgba(92,92,92,0); 
    box-shadow: 5px 5px 15px 5px #FF8080, -9px 5px 15px 5px #FFE488, -7px -5px 15px 5px #8CFF85, 12px -5px 15px 5px #80C7FF, 12px 10px 15px 7px #E488FF, -10px 10px 15px 7px #FF616B, -10px -7px 27px 1px #8E5CFF, 13px 12px 15px 5px rgba(92,92,92,0);
}
.CV {
    width: 70%;
    height: auto;
    border: none;
    position: relative;
}
#description > button {
    width: 50%;
    padding: 1%;
    background-color: rgb(245, 232, 224);
    border: none;
    z-index: 2;
}
#description {
    margin-top: 20%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    font-weight: 500;
    border: 1%;

}
#description p {
    animation: paragraphs 2s forwards;
    padding: 5%;
    font-size: 1.2rem;
}
.quill {
    width: 10vw;
}
h3, h2{
    font-family: 'Monoton';
}
h2 {
    margin: auto;
    font-size: 5rem;
    padding: 5%;
}
#interests {
    width: 100vw;
    display: flex;
    flex-direction: column;
}
#galerie {
    width: 100vw;
    height: 50%;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
}
.galerieCard {
    display: flex;
}
.chess {
    background-image: url('../assets/chess.png');
    background-size: cover;
    color: white;
    width: 50vw;
}
.chess_astro {
    display: flex;
    flex-direction: row;
    width: 100vw;
}
.astro {
    background-image: url('../assets/earth.jpeg');
    background-size: cover;
    color: white;
    display: flex;
    flex-direction: column;
    height: 50vh;
    width: 50vw;
}
.astro p {
    width: 20%;
}
.bball {
    display: flex;
    background-color: black;
    color: white;
    height: 60vh;
}
.bball img {
    object-fit: cover;
}
.bballText {
    text-align: center;
    width: 100%;
    height: 100%;
}
.bballText img {
    height: 60%;
}
.books {
    background-image: url("../assets/books.jpeg");
    background-size: cover;
    color: white;
}
.books p {
    background-color: rgb(1,1,1, 0.6);
}
.portraitTtl {
    width: 100%;
    position: relative;
    padding-top: 20vh;
}
.portraitTtl {
    margin: auto;
    position: relative;
}
#languageBtn button {
background-color: white;
border-radius: 50%;
padding: 1%;
position: fixed;
top: 1%;
right: 1%;
}
.changeLanguage {
    animation: changeLanguage 1s forwards;
}

/*********************************************
****************CAROUSEL ********************
**********************************************/

.carousel {
    width: 100vw;
    height: 80vh;
    position: relative
}
.carousel > ul {
    margin: 0;
    padding: 0;
    list-style: none;
}
.carousel > li {
    width: 100vw;
    overflow: hidden;
}
.slide {
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: 200ms opacity ease-in-out;
    transition-delay: 200ms;
}
.slide[data-active] {
    opacity: 1;
    z-index: 1;
    transition-delay: 0ms;
}
.slide > img {
    display: block;
    margin: auto;
    height: 100%;
    object-fit: cover;
    object-position: center;
    max-width: 100%;
}
.carousel-button {
    position: absolute;
    background: none;
    border: none;
    font-size: 5rem;
    z-index: 99;
    top: 50%;
    transform: translateY(-50%);
    color: rgb(245, 232, 224);
    cursor: pointer;
    border-radius: .25rem;
    padding: 0 .5rem;
    background-color: rgba(0, 0, 0, .1);
}
.carousel-button:hover, 
.carousel-button:focus {
    color: #80C7FF;
    background-color: rgba(0, 0, 0, .2);
}
.carousel-button.prev {
    left: 1rem;
}
.carousel-button.next {
    right: 1rem;
}


#Title {
    font-family: 'Monoton';
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    height: 5vh;
    margin-top: 50px;
    padding-right: 5% ;

}
h3 {
    font-size: 2vw;
}
ul {
    display: flex;
    flex-direction: row;
    list-style: none;
}
li {
    font-family: Monoton;
    font-size: 4vw;
}
li:hover {
    animation: letters 0.5s forwards;
}
.letters:hover {
    animation: letters 0.5s ease-in-out
}

/************************************
************* ANIMATIONS ************
*************************************/

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
@keyframes letters {
    from {
        transform: translateY(0);
    }
    to {
        transform: translateY(-1vh);
        color: rgb(31, 29, 29);
    }
}

/************************************
************* RESPONSIVE*************
*************************************/

@media only screen and (min-width: 769px) {
    #description {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    text-align: center;
    align-items: center;
    font-weight: 500;
    border: 1%;
    }
}

@media only screen and (min-width: 1224px) {
    #resume {
        width: 80vw;
    }

}
@media only screen and (max-width: 769px) {
    .astro p {
        width: 50vw;
    }
    .bball {
    display: flex;
    flex-direction: column;
    background-color: white;
    height: 80vh;
    }
    .books {   
        margin: auto;
        padding: 10% 0;
        display: flex;
        flex-direction: column;
    }
    .bballText {
        text-align: center;
        justify-content: center;
        align-items: center;
    }
    .portrait {
        flex-direction: column;
        padding: 20% 0;
        align-items: center;
        height: auto;
    }
    .portraitTitle {
        position: relative !important;
        margin: auto;
        padding-bottom: 10%;
        font-size: 2rem;
    }
    .portrait p {
        width: 80vw;
        text-align: start;
    }
    .portrait img {
        width: 50vw;
    }
    .portraitImg {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    h2 {
        font-size: 2.5rem;
    }
}

/***************************** */

@media only screen and (max-width: 720px) {
    .slide > img {
        display: block;
        width: auto;
        margin: auto;
        object-fit: scale-down;
    }
}
</style>