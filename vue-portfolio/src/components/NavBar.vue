<template>
    <header id="navbar">
        <nav >
            <a class="logo" href="#hello">franeguerrero</a>

            <ul>
                <li><a href="#about">{{ aboutText }}</a></li>
                <li><a href="#work">{{ worksText }}</a></li>
                <li><a href="#skills">{{ skillsText }}</a></li>
                <li><a href="#contact">{{ contactText }}</a></li>

                <button @click="toggleLanguage">
                    <img :src="currentFlag" alt="Language Flag" style="width: 30px; height: auto; cursor: pointer;">
                </button>
            </ul>
        </nav>
    </header>
</template>

<script setup lang="ts">
//Importaciones
import { ref, computed, defineProps, defineEmits } from 'vue';
import usaFlag from '@/assets/united-states.png';
import argentinaFlag from '@/assets/argentina.png';

// Propiedades y emisores
const props = defineProps<{ currentLanguage: string }>();
const emit = defineEmits();

// Variables reactivas y computadas
const currentLanguage = ref<string>(props.currentLanguage);
const currentFlag = computed(() => currentLanguage.value === 'usa' ? usaFlag : argentinaFlag);

const aboutText = computed(() => currentLanguage.value === 'usa' ? 'About me' : 'Sobre mí');
const worksText = computed(() => currentLanguage.value === 'usa' ? 'Projects' : 'Proyectos');
const skillsText = computed(() => currentLanguage.value === 'usa' ? 'Skills' : 'Habilidades');
const contactText = computed(() => currentLanguage.value === 'usa' ? 'Contact' : 'Contacto');


// Funciones
const toggleLanguage = () => {
    const newLang = currentLanguage.value === 'usa' ? 'argentina' : 'usa';
    currentLanguage.value = newLang;
    emit('change-language', newLang);
};


document.addEventListener("DOMContentLoaded", function() {
  const navbar = document.getElementById("navbar");
  if (navbar) {
    document.addEventListener("scroll", function() {
      if (window.scrollY > 50) {
        navbar.classList.add("opaque");
      } else {
        navbar.classList.remove("opaque");
      }
    });
  }
});

document.addEventListener('DOMContentLoaded', function() {
    const navbarLinks = document.querySelectorAll('#navbar a[href^="#"]');
    
    navbarLinks.forEach(function(link) {
        link.addEventListener('click', function(event) {
            event.preventDefault();
            const targetId = (event.currentTarget as HTMLElement).getAttribute('href')?.substring(1);
            const targetElement = document.getElementById(targetId!);
            if (targetElement) {
                const elementHeight = targetElement.offsetHeight;
                const offset = targetElement.offsetTop;

                if(elementHeight < window.innerHeight){

                    const centerOffset = offset - (window.innerHeight / 2) + ( elementHeight / 2) - 40;
                    
                    window.scrollTo({
                        top: centerOffset,
                        behavior: 'smooth'
                    });
                } else {
                    const topOffset = offset - 80;

                    window.scrollTo({
                        top: topOffset,
                        behavior: 'smooth'
                    });
                }
            }
        });
    });
});

</script>

<style scoped>
header {
    color: #FFF;
    font-family: 'Ubuntu', sans-serif;
    display: flex;
    height: 80px;
    position: fixed;
    top: 0;
    width: 99.14vw;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    transition: .3s;
}

header.opaque{
    background-color: #141414;

}

.logo {
    font-weight: 900;
    font-size: 40px;
    cursor: pointer;
    user-select: none;
}
a{
    color: #FFF;
    background: none;
}


li {
    text-decoration: none;
    font-weight: 300;
    font-size: 20px;
    cursor: pointer;
    user-select: none;
    display: inline-block;
    vertical-align: middle;
    -webkit-transform: perspective(1px) translateZ(0);
    transform: perspective(1px) translateZ(0);
    box-shadow: 0 0 1px rgba(0, 0, 0, 0);
    position: relative;
    overflow: hidden;
}

li:before {
    content: "";
    position: absolute;
    z-index: -1;
    left: 51%;
    right: 51%;
    bottom: 0;
    background: #FFF;
    height: 1px;
    -webkit-transition-property: left, right;
    transition-property: left, right;
    -webkit-transition-duration: 0.2s;
    transition-duration: 0.2s;
    -webkit-transition-timing-function: ease-out;
    transition-timing-function: ease-out;
}

li:hover:before,
li:focus:before,
li:active:before {
    left: 0;
    right: 0;
}

ul {
    list-style-type: none;
    width: 45%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

nav {
    width: 60vw;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

button {
    background-color: transparent;
    border: none;
    transition: .2s;
}
button:hover{
    scale: 1.3;
}
</style>