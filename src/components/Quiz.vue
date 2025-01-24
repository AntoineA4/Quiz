<template>
    <div>
        <h1>{{ quiz.title }}</h1>
        <ProgressionBar :value="step" :max = "quiz.questions.length - 1" />
        <Question :question="question" v-if="question" />
    </div>

</template>

<script setup>
import { computed, ref } from 'vue';
import  ProgressionBar from './ProgressionBar.vue';
import Question from './Question.vue';


const props = defineProps({
    quiz: Object
})
const step =ref(0)
const question = computed (() => props.quiz.questions[step.value])
</script>