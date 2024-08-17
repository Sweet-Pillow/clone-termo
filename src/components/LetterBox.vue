<script setup>

const props = defineProps(['letra'])

</script>

<template>
    <div class="font-bold size-10 border border-black flex justify-center items-center text-2xl select-none">
        {{ props.letra }}
    </div>
</template>