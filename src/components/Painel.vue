<script setup>

import { ref } from "vue"
import LetterRow from "./LetterRow.vue"
const word = "TERMO"

const currentIndexRow = ref(0)

</script>

<template>
    <div class="h-4/5 border border-red-700 p-4">
        <LetterRow v-for="(_, index) in 6" :indexRow="index" :currentIndexRow="currentIndexRow"></LetterRow>
    </div>
</template>