<script setup>
import { ref } from "vue"
import LetterBox from "./LetterBox.vue"

const props = defineProps(['lineIndex', 'palavraCerta'])

const selectedBox = ref(0)

const handleSelectedBox = (clickedIndex = -1) => {

    if (clickedIndex > -1) {
        selectedBox.value = clickedIndex
    } else if (selectedBox.value < 4) {
        selectedBox.value = selectedBox.value + 1
    }
}

</script>

<template>
    <div class="flex flex-row gap-4 pb-4">
        <LetterBox v-for="(letra, index) in 5" :index="index" :letra="letra" :selectedBox="selectedBox"
            @handleSelectedBox="handleSelectedBox"></LetterBox>
    </div>
</template>