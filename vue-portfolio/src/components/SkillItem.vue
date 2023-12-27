<template>
    <div class="skill-item">
      <img :src="logo" alt="Skill Logo" class="skill-logo" loading="lazy">
      <h3 class="skill-name">{{ name }}</h3>
    </div>
  </template>
  
  <script setup lang="ts">
  import { defineProps } from 'vue';
  
  const { name, logo } = defineProps<{
    name: string;
    logo: string;
  }>();
  </script>
  
  <style scoped>
  .skill-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10px;
    padding: 10px;
  }
  
  .skill-logo {
    width: 100px;
    height: 100px;
    margin-bottom: 10px;
  }

  
  .skill-name {
    font-size: 1.2rem;
  }
  </style>
  