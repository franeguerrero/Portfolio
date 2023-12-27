<template>
    <div class="hiArea">
        <div class="glass">
            <div class="text">
                <div class="title">
                    <h2>{{ greetText }}</h2>
                </div>
                <h1>{{ descriptionText }}</h1>
            </div>
            <img :src="myImage" alt="This gorgeous man is me." id="pic">
        </div>
        <ChevronDown class="chevron"/>
    </div>
</template>

<script setup lang="ts">
import { ref, defineProps, computed, watch } from 'vue';
import ChevronDown from './ChevronDown.vue';
import myImage from '@/assets/FacePNG.png';

const props = defineProps<{
  currentLanguage: string;
}>();

const currentLanguage = ref(props.currentLanguage);

watch(() => props.currentLanguage, (newValue) => {
  currentLanguage.value = newValue;
});


const greetText = computed(() => currentLanguage.value === 'usa' ? "Hi! I'm Fran" : "¡Hola! Soy Fran");
const descriptionText = computed(() => currentLanguage.value === 'usa' ? "I'm the web developer and UX/UI designer you were looking for." : "Soy el desarrollador web y diseñador UX/UI que estabas buscando.");

</script>


<style scoped>

.chevron{
    bottom: 3vh;
}
.hiArea {
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}

h2 {
    font-weight: 900;
    font-size: 4rem;
}

h1 {
    font-size: 2rem;
    width: 80%;
}

.text {
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
    left: 5rem;
}

.glass {
    border-radius: 25px;
    background-color: #141414;
    box-shadow: 10px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    height: 22rem;
    width: 60vw;

}

.glass #pic {
    position: relative;
    bottom: 10.1rem;
    right: 0;
    height: 32rem;
    filter: drop-shadow(-6px 8px 10px rgba(0, 0, 0, 0.47)) drop-shadow(6px 8px 10px rgba(0, 0, 0, 0.47));
    border-radius: 0px 0px 25px 0px;
}

.title{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 67%;
    margin-bottom: 10px;
}
</style>