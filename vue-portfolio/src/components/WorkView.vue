<template>
  <div class="workArea">
      <h2>{{ workTitle }}</h2>
      <WorkCard :projectDetails="projectDetails[0]" />
      <WorkCard :projectDetails="projectDetails[1]" />
      <WorkCard :projectDetails="projectDetails[2]" />
  </div>

</template>

<script setup lang="ts">
import {computed, ref, watch } from 'vue';
import WorkCard from "./WorkCard.vue";
import LemonLane from '@/assets/lemonlane.png'

const props = defineProps<{
currentLanguage: string;
}>();

const currentLanguage = ref(props.currentLanguage);

// Observa los cambios en la prop currentLanguage
watch(() => props.currentLanguage, (newValue) => {
currentLanguage.value = newValue;
});

// Definición de los detalles de los proyectos según el idioma
const projectDetails = computed(() => {
if (currentLanguage.value === 'usa') {
  return [
    { name: 'LemonLane', description: 'LemonLane is a personal project with a friend, the concept of an online vintage clothing store. We created our own CMS system that facilitates product management and inventory control. With LemonLane, we fuse the fashion of the past with modern tools, reflecting our entrepreneurial spirit and passion for vintage.', link: 'https://lemon-lane.vercel.app/', imageSrc: LemonLane},
    { name: 'Template 1', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime nesciunt ullam, sequi autem numquam culpa voluptatibus consectetur cupiditate tenetur harum, debitis modi officia tempore quisquam quaerat dicta expedita impedit nobis accusamus veniam quam rem! Perferendis, corrupti? Totam explicabo harum ut! Eos, illum!', link: '#', imageSrc: LemonLane },
    { name: 'Template 2', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime nesciunt ullam, sequi autem numquam culpa voluptatibus consectetur cupiditate tenetur harum, debitis modi officia tempore quisquam quaerat dicta expedita impedit nobis accusamus veniam quam rem! Perferendis, corrupti? Totam explicabo harum ut! Eos, illum!', link: '#', imageSrc: LemonLane }
  ];
} else {
  return [
    { name: 'LemonLane', description: 'LemonLane es un proyecto personal junto a un amigo, el concepto de una tienda de ropa vintage en línea. Creamos un sistema CMS propio que facilita la gestión de productos y control de inventario. Con LemonLane, fusionamos la moda del pasado con herramientas modernas, reflejando nuestro espíritu emprendedor y pasión por lo vintage.', link: '#', imageSrc: LemonLane},
    { name: 'Plantilla 1', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime nesciunt ullam, sequi autem numquam culpa voluptatibus consectetur cupiditate tenetur harum, debitis modi officia tempore quisquam quaerat dicta expedita impedit nobis accusamus veniam quam rem! Perferendis, corrupti? Totam explicabo harum ut! Eos, illum!', link: '#', imageSrc: LemonLane },
    { name: 'Plantilla 2', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Maxime nesciunt ullam, sequi autem numquam culpa voluptatibus consectetur cupiditate tenetur harum, debitis modi officia tempore quisquam quaerat dicta expedita impedit nobis accusamus veniam quam rem! Perferendis, corrupti? Totam explicabo harum ut! Eos, illum!', link: '#', imageSrc: LemonLane }
  ];
}
});

const workTitle = computed(() => currentLanguage.value === 'usa' ? "Some of my projects" : "Algunos de mis proyectos");
</script>

<style scoped>
.workArea {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin-top: 200px;
    padding-top: 80px;
}

@media (prefers-reduced-motion: no-preference){
  .card{
    scale: .6; opacity: 0;
    animation: fade-in linear forwards;
    animation-timeline: view();
    animation-range: 150px 450px;
  }

  @keyframes fade-in {
    to {scale: 1; opacity: 1;}
    
  }
}
</style>