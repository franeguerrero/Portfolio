<template>
    <div class="aboutArea">
      <h2>{{ aboutTitle }}</h2>
      <br>
      <p>{{ aboutText1 }} <b>Keep it Simple</b>.</p>
      <p>{{ aboutText2 }}</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, computed, watch } from 'vue';
  
  const props = defineProps<{
    currentLanguage: string;
  }>();
  
  const currentLanguage = ref(props.currentLanguage);
  
  watch(() => props.currentLanguage, (newValue) => {
    currentLanguage.value = newValue;
  });
  
  const aboutTitle = computed(() => currentLanguage.value === 'usa' ? 'About me' : 'Sobre mí');
  const aboutText1 = computed(() => {
    return currentLanguage.value === 'usa'
      ? 'My design and development philosophy is clear:'
      : 'Mi filosofía de diseño y desarrollo es clara:';
  });
  
  const aboutText2 = computed(() => {
    return currentLanguage.value === 'usa'
      ? 'Throughout my career, I have observed how simplicity can transform a good idea into an excellent user experience. I constantly look for ways to simplify and optimize, making sure that every element in an interface or digital solution serves a specific purpose and improves overall usability. I firmly believe that by cutting through the noise and focusing on the essentials, we can create products and experiences that are intuitive, efficient, and memorable for users.'
      : 'A lo largo de mi carrera he observado cómo la sencillez puede transformar una buena idea en una excelente experiencia de usuario. Busco constantemente formas de simplificar y optimizar, asegurándome de que cada elemento de una interfaz o solución digital sirva a un propósito específico y mejore la usabilidad general. Creo firmemente que eliminando el ruido y centrándonos en lo esencial, podemos crear productos y experiencias intuitivos, eficientes y memorables para los usuarios.';
  });
  </script>
  
  <style scoped>
  .aboutArea {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  
  h2 {
    font-weight: 900;
    font-size: 3rem;
  }
  
  p {
    text-align: center;
    font-size: 1.5rem;
    width: 60%;
  }
  
  b {
    font-weight: 600;
  }
  </style>
  