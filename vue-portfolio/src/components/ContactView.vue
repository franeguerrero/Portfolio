<template>
  <div class="wrapper">
    <div class="contactContainer">
      <h2>{{contactTitle}}</h2>

      <form @submit.prevent="submitForm" class="formFlexContainer">
        <div class="formGroup">
          <input type="text" v-model="name" :placeholder="namePlaceholder" required/>
        </div>

        <div class="formGroup">
          <input type="email" v-model="email" :placeholder="emailPlaceholder" required/>
        </div>

        <div class="formGroup">
          <input type="text" v-model="subject" :placeholder="subjectPlaceholder" required/>
        </div>

        <div class="formGroup">
          <textarea v-model="message" :placeholder="messagePlaceholder" required></textarea>
        </div>

        <button type="submit">{{ submitButtonText }}</button>
      </form>

      <div class="socialIcons">
        <a href="https://github.com/franeguerrero" target="_blank" rel="noopener noreferrer">
          <i class="fab fa-github"></i>
        </a>
        <a href="https://www.linkedin.com/in/franeguerrero/" target="_blank" rel="noopener noreferrer">
          <i class="fab fa-linkedin"></i>
        </a>
        <a href="https://dribbble.com/franeguerrero" target="_blank" rel="noopener noreferrer">
          <i class="fab fa-dribbble"></i>
        </a>
      </div>
    </div>
    
    <footer>
    <p class="footerText">Francisco Guerrero 2023 &copy; {{footerText}}</p>
    </footer>
  
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

const contactTitle = computed(() => currentLanguage.value === 'usa' ? 'Get in touch!' : '¡Ponte en contacto!');
const namePlaceholder = computed(() => currentLanguage.value === 'usa' ? 'Your Name' : 'Tu Nombre');
const emailPlaceholder = computed(() => currentLanguage.value === 'usa' ? 'Email' : 'Correo electrónico');
const subjectPlaceholder = computed(() => currentLanguage.value === 'usa' ? 'Subject' : 'Asunto');
const messagePlaceholder = computed(() => currentLanguage.value === 'usa' ? 'Message' : 'Mensaje');
const submitButtonText = computed(() => currentLanguage.value === 'usa' ? 'Submit' : 'Enviar');
const footerText = computed(() => currentLanguage.value === 'usa' ? 'All rights reserved.' : 'Todos los derechos reservados.');


const name = ref('')
const email = ref('')
const subject = ref('')
const message = ref('')

const submitForm = () => {
  const formData = {
    name: name.value,
    email: email.value,
    subject: subject.value,
    message: message.value
  }

  console.log('Form Data:', formData)
  // Implementa tu lógica de envío aquí
}
</script>
<style scoped>
.contactContainer {
  width: 100%;
  background-color: #141414;
  height: calc(100vh - 80px - 2rem);
  margin-top: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.formFlexContainer {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.formGroup {
  margin-bottom: 20px;
  width: 40vw;
}

input[type='text'],
input[type='email'],
textarea {
  font-size: 1.2rem;
  width: 100%;
  padding: 1rem;
  background-color: transparent;
  border: none;
  border-radius: 6px 6px 0 0;
  border-bottom: 2px solid white; 
  color: white;
  outline: none;
  transition: border-bottom-color .3s; 
  resize: none;
}

textarea{
  padding: 1rem 0 4rem 1rem;
}

input[type='text']:focus,
input[type='email']:focus,
textarea:focus {
  border-bottom-color: #784fd6; 
  background-color: #0002;
}

button {
  align-self: center;
  margin: 1rem;
  padding: 1rem 5rem;
  background-color: #572fb4;
  font-size: 1rem;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: 0.2s;
}

button:hover {
  background-color: #3a1c81;
}


a{
  background-color: transparent;
}


.socialIcons {
  margin-top: 3rem; 
  display: flex;
  gap: 3rem;
}

.socialIcons a .fab{
  font-size: 2rem;
  color: gray;
  transition: color 0.3s;
}

.socialIcons a:hover .fab{
  color: #572fb4;
}


footer{
    background-color: #141414;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 2rem;
}
.footerText{
    color: grey;
}
</style>