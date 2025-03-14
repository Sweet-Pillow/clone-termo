<script setup>
import { ref } from "vue"
import LetterBox from "./LetterBox.vue"

const props = defineProps(['lineIndex', 'word'])

const selectedBox = ref(0)

const handleSelectedBox = (clickedIndex = -1, move = 1) => {

    if (clickedIndex > -1) {
        selectedBox.value = clickedIndex
    } else if (selectedBox.value + move < 5 & selectedBox.value + move > -1) {
        selectedBox.value = selectedBox.value + move
    }

}

</script>

<template>
    <div class="flex flex-row gap-4 pb-4">
        <LetterBox v-for="(letter, index) in 5" :index="index" :letter="letter" :selectedBox="selectedBox"
            @handleSelectedBox="handleSelectedBox"></LetterBox>
    </div>
</template>