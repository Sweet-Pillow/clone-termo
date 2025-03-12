<script setup>
import LetterBox from "./LetterBox.vue"

const props = defineProps(['lineIndex', 'palavraCerta'])
</script>

<template>
    <div class="flex flex-row gap-4 pb-4">
        <LetterBox v-for="(letra, index) in 5" :index="index" :letra="letra"></LetterBox>
    </div>
</template>