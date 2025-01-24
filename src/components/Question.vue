<template>
    <div :class="question">
        <h3>{{ question.question }}</h3>
        <ul>
            <li v-for="(choice, index) in question.choices" :key="choice">
                <label :for="`answer${index}`">
                    <input :id="`answer${index}`" type="radio" name="answer">
                    {{ choice }}
                </label>
            </li>
        </ul>
        <button>Next Question</button>
    </div>
    
</template>

<script setup>
const props = defineProps ( {
    question : Object
})

</script>