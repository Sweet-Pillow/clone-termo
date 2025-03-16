<script setup>
import { ref } from 'vue'

const props = defineProps(['indexLetter', 'currenIndextLetter', 'isCurrentRow'])
const emit = defineEmits(['handleChangeFocus'])

const letter = ref('')

const handleClick = (event) => {
    emit('handleChangeFocus', event, props.indexLetter)

}

const handleKeydown = (event) => {
    const regex = /^[a-zA-ZÀ-ÖØ-öø-ÿÇç]$/

    if (regex.test(event.key) || event.key == 'Backspace') {

        letter.value = event.key !== 'Backspace' ? event.key.toUpperCase() : ''
        emit('handleChangeFocus', event, props.indexLetter)
    }

}

</script>
<template>
    <div tabindex="0" @click="handleClick" @keydown="handleKeydown"
        class="font-bold size-10 border border-black flex justify-center items-center text-2xl select-none "
        :class="{ ' border-b-4': isCurrentRow & (indexLetter == currenIndextLetter) }">
        {{ letter }}
    </div>
</template>