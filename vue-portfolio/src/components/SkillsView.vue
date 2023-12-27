<template>
    <div class="skillsArea">
        <h2>{{skillsTitle}}</h2>
        <div class="skillList">
            <SkillItem v-for="skill in skills" :key="skill.name" :name="skill.name" :logo="skill.logo" />
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue';
import VueJSLogo from '@/assets/skills/vuejs.svg';
import TypescriptLogo from '@/assets/skills/typescript.svg';
import JavascriptLogo from '@/assets/skills/javascript.svg';
import HTMLLogo from '@/assets/skills/html.svg';
import CSSLogo from '@/assets/skills/css.svg';
import FigmaLogo from '@/assets/skills/figma.svg';
import NestJSLogo from '@/assets/skills/nestjs.svg';
import JestLogo from '@/assets/skills/jest.svg';
import NodeJSLogo from '@/assets/skills/nodejs.svg';
import PostgreSQLLogo from '@/assets/skills/postgresql.svg';
import MySQLLogo from '@/assets/skills/mysql.svg';
import GitLogo from '@/assets/skills/git.svg';
import SkillItem from './SkillItem.vue';
  
  const props = defineProps<{
    currentLanguage: string;
  }>();
  
  const currentLanguage = ref(props.currentLanguage);
  
  watch(() => props.currentLanguage, (newValue) => {
    currentLanguage.value = newValue;
  });
  
  const skillsTitle = computed(() => currentLanguage.value === 'usa' ? 'Skills' : 'Habilidades');

const skills = ref([
    { name: 'VueJS', logo: VueJSLogo },
    { name: 'Typescript', logo: TypescriptLogo },
    { name: 'Javascript', logo: JavascriptLogo },
    { name: 'HTML', logo: HTMLLogo },
    { name: 'CSS', logo: CSSLogo },
    { name: 'Figma', logo: FigmaLogo },
    { name: 'NestJS', logo: NestJSLogo },
    { name: 'Jest', logo: JestLogo },
    { name: 'NodeJS', logo: NodeJSLogo },
    { name: 'PostgreSQL', logo: PostgreSQLLogo },
    { name: 'MySQL', logo: MySQLLogo },
    { name: 'Git', logo: GitLogo }
]);
</script>

<style scoped>
.skillsArea {
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    margin-top: 200px;
}

.skillList {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    width: 60%;
    gap: 20px;
    margin-top: 100px;
}

h2 {
    font-weight: 900;
    font-size: 3rem;
}

p {
    font-size: 1.5rem;
    width: 60%;
}
</style>