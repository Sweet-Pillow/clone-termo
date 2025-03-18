<script setup>
import { ref } from "vue"
import LetterBox from "./LetterBox.vue"

const props = defineProps(['indexRow', 'currentIndexRow'])

const currenIndextLetter = ref(0)

const letters = [
    ref(''),
    ref(''),
    ref(''),
    ref(''),
    ref(''),
]

const isCurrentRow = ref(props.indexRow == props.currentIndexRow)

const handleChangeFocus = (event, index) => {
    
    // Function to manager the focus when clicked
    if(event.type == "click"){
        currenIndextLetter.value = index
        return
    }

    // Functions to manager the focus when the key is pressed
    if (event.key != "Backspace") {
        if (currenIndextLetter.value + 1 < 5) {
            currenIndextLetter.value++
            event.target.nextElementSibling.focus()
        }

    } else {
        if (currenIndextLetter.value - 1 > -1) {
            currenIndextLetter.value--
            event.target.previousElementSibling.focus()
        }
    }

}

</script>

<template>
    <div class="flex flex-row gap-4 pb-4">
        <LetterBox v-for="(_, index) in 5" @handleChangeFocus="handleChangeFocus" :indexLetter="index"
            :currenIndextLetter="currenIndextLetter" :isCurrentRow="isCurrentRow"></LetterBox>
    </div>
</template>