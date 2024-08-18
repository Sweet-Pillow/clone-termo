<script setup>
import { ref } from 'vue'

const props = defineProps(['letra', 'index'])

const clicked = ref(false)
const letter = ref("")

const selectLetter = () => {
    clicked.value = true
}

const handleBlur = () => {
    clicked.value = false
}

const getLetter = (event) => {
    const regex = /^[a-zA-Z\s]$/;
    regex.test(event.key)? letter.value = event.key.toUpperCase(): ""
    console.log(event.key)
}

</script>

<template>
    <div @click="selectLetter" @keyup="getLetter" @blur="handleBlur" tabindex="0" class="font-bold size-10 border border-black flex justify-center items-center text-2xl select-none ":class="{' border-b-4': clicked}">
        {{ letter }}
    </div>
</template>