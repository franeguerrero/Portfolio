<!-- Componente principal -->
<template id="app">
  <main>
    <!-- Sección de vistas -->
    <div id="hello"><HelloView :currentLanguage="currentLanguage" /></div>
    <div id="about"><AboutView :currentLanguage="currentLanguage" class="view"/></div>
    <div id="work"><WorkView :currentLanguage="currentLanguage" class="view" /></div>
    <div id="skills"><SkillsView :currentLanguage="currentLanguage" class="view"/></div>
    <div id="contact"><ContactView :currentLanguage="currentLanguage"/></div>
    
    <!-- Barra de navegación -->
    <NavBar :currentLanguage="currentLanguage" @change-language="updateLanguage" />

    <!-- Fondo -->
    <BackGround />
  </main>
</template>

<script setup lang="ts">
// Importaciones
import { ref } from 'vue';
import NavBar from './components/NavBar.vue';
import BackGround from './components/BackGround.vue';
import HelloView from './components/HelloView.vue';
import WorkView from './components/WorkView.vue';
import AboutView from './components/AboutView.vue';
import SkillsView from './components/SkillsView.vue';
import ContactView from './components/ContactView.vue';

// Variables reactivas y funciones
const currentLanguage = ref<string>('usa');

const updateLanguage = (newLang: string) => {
    currentLanguage.value = newLang;
};
</script>

<style>
/* Fuentes y estilos globales */
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@300;700&display=swap');
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css');

/* Estilos generales */
* {
  color: #FFF;
  font-family: 'Ubuntu', sans-serif;
  scroll-snap-type: y mandatory;
  scroll-behavior: smooth;
  max-width: calc(100vw - (100vw - 100%)) !important;
}

/* Estilos específicos para h2 */
h2 {
  font-weight: 900;
  font-size: 3rem;
}

/* Estilos para la aplicación y vistas */
#app {
  display: flex;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

/* Estilos de animación */
@media (prefers-reduced-motion: no-preference) {
  .view {
    scale: .6; 
    opacity: 0;
    animation: fade-in linear forwards;
    animation-timeline: view();
    animation-range: 150px 450px;
  }

  @keyframes fade-in {
    to {
      scale: 1; 
      opacity: 1;
    }
  }
}
</style>
