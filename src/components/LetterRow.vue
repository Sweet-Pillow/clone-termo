<script setup>
import { ref } from "vue"
import LetterBox from "./LetterBox.vue"

const props = defineProps(['indexRow', 'currentIndexRow'])

const currenIndextLetter = ref(0)

let isCurrentRow = props.indexRow == props.currentIndexRow

const handleChangeFocus = (event) => {

    if(event.key != "Backspace"){   
        currenIndextLetter.value ++
        event.target.nextElementSibling.focus()

    } 

}

</script>

<template>
    <div class="flex flex-row gap-4 pb-4">
        <LetterBox v-for="(_, index) in 5" @handleChangeFocus="handleChangeFocus"
        :indexLetter="index" :currenIndextLetter="currenIndextLetter" :isCurrentRow="isCurrentRow"></LetterBox>
    </div>
</template>