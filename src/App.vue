<template>
  <div v-if="state === 'error'">
    <p>Impossible de charger le quiz</p>
  </div>
  <div :aria-busy="state === 'loading'">
    <quizComponent :quiz ="quiz" v-if="quiz" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import quizComponent from './components/quiz.vue';

const quiz = ref(null)
const state = ref('loading')
onMounted(() => {
  fetch('/Quiz.json') 
    .then(r => {
        if (r.ok) {
            return r.json()
        }
        throw new Error ('Impossibme de récupérer le json')
    }) 
    .then (data => {
        quiz.value = data 
        state.value = 'idle'
    })
    .catch (e => {
        state.value = 'error'
    })
    
});
</script>
