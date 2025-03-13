<script setup>
import { ref } from 'vue'

const props = defineProps(['letra', 'index', 'selectedBox'])

const letter = ref("")

const emit = defineEmits(['handleSelectedBox'])

const selectLetter = () => {
    emit('handleSelectedBox', props.index)

}


const getLetter = (event) => {
    const regex = /^[a-zA-Z\s]$/;
    regex.test(event.key)? letter.value = event.key.toUpperCase(): ""
    
    // const currentElement = 
    const brother = event.target.nextElementSibling

    if (brother) {
        brother.focus()
    }

    emit('handleSelectedBox')
}

</script>
<template>
    <div @click="selectLetter" @keydown="getLetter" tabindex="0" class="font-bold size-10 border border-black flex justify-center items-center text-2xl select-none ":class="{' border-b-4': (props.selectedBox == props.index)}">
        {{ letter }}
    </div>
</template>