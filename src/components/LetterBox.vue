<script setup>
import { ref } from 'vue'

const props = defineProps(['letter', 'index', 'selectedBox', 'verifyLetters', 'word'])

const letter = ref("")

const emit = defineEmits(['handleSelectedBox'])

const selectLetter = () => {
    emit('handleSelectedBox', props.index)

}

const handleGetLetter = (event) => {
    const regex = /^[a-zA-Z\s]$/;
    regex.test(event.key) ? letter.value = event.key.toUpperCase() : ""
}

const changeFocus = (event) => {
    if (event.key != "Backspace") {

        const brother = event.target.nextElementSibling

        if (brother) {
            brother.focus()
        }

        emit('handleSelectedBox')

    } else {

        letter.value = ""

        const brother = event.target.previousElementSibling

        if (brother) {
            brother.focus()
        }

        emit('handleSelectedBox', -1, -1)
    }
}

const getLetter = (event) => {
    if (event.key != "Enter") {

        handleGetLetter(event)
        changeFocus(event)

    }
}

const verify = (v) => {
    if(v & letter.value == props.letter){
        return 1
    } else if(v & props.word.includes(letter.value)){
        return 2
    } else if(v){
        return 3
    }
}

</script>
<template>
    <div @click="selectLetter" @keydown="getLetter" tabindex="0"
        class="font-bold size-10 border border-black flex justify-center items-center text-2xl select-none "
        :class="{ ' border-b-4': (props.selectedBox == props.index), ' bg-green-400': verify(verifyLetters) == 1, ' bg-yellow-400': verify(verifyLetters) == 2, ' bg-gray-400': verify(verifyLetters) == 3}">
        {{ letter }}
    </div>
</template>