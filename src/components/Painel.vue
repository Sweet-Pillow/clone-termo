<script setup>
    import LetterBox from "./LetterBox.vue"
    const palavra = "TERMO"
</script>

<template>
    <div class="h-4/5 border border-red-700 p-4">
        <div class="flex flex-row gap-4 pb-4" v-for="_ in 5">

            <LetterBox v-for="letra in palavra" :letra="letra"></LetterBox>
        </div>
    </div>
</template>