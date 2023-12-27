<template>
    <div class="card">
        <img data-role="img" :src="projectDetails.imageSrc" :alt="projectDetails.name" loading="lazy">
        <div class="data">
            <h3>{{ projectDetails.name }}</h3>
            <br>
            <p>{{ projectDetails.description }}</p>
            <br>
            <a :href="projectDetails.link" target="_blank">{{ projectDetails.name }}</a>
        </div>
    </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps<{
  projectDetails: {
    name: string;
    description: string;
    link: string;
    imageSrc: string;
  };
}>();

console.log(props.projectDetails.imageSrc)
</script>

<style scoped>
.card{
    width: 60%;
    background-color: #141414;
    display: flex;
    flex-direction: row;
    border-radius: 25px;
    align-items: center;
    justify-content: space-between;
    margin-top: 100px;
}

.data{
    display: flex;
    flex-direction: column;
    align-items: center;
}

.data h3 {
    font-weight: 900;
    font-size: 3rem;
}

.data p {
    font-size: 1.2rem;
    width: 80%;
}
.data a {
    font-size: 1.5rem;
    width: 80%;
    text-align: center;
    color: #784fd6;
    background-color: transparent;
    border-radius: 6px;
}

img{
    width: 60%;
    border-radius: 25px 0 0 25px ;
}

</style>