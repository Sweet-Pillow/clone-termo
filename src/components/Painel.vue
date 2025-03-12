<script setup>
import LetterRow from "./LetterRow.vue"
const palavra = "TERMO"
</script>

<template>
    <div class="h-4/5 border border-red-700 p-4">
        <LetterRow v-for="(_, index) in 6" :lineIndex="index" :palavraCerta="palavra"></LetterRow>
    </div>
</template>