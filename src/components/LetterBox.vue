<script setup>
import { ref } from 'vue'

const props = defineProps(['letter', 'index', 'selectedBox'])

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

</script>
<template>
    <div @click="selectLetter" @keydown="getLetter" tabindex="0"
        class="font-bold size-10 border border-black flex justify-center items-center text-2xl select-none "
        :class="{ ' border-b-4': (props.selectedBox == props.index) }">
        {{ letter }}
    </div>
</template>