<template>
    <v-btn> {{ etiqueta }} </v-btn>
</template>

<script setup>
import { ref } from 'vue';
const props = defineProps({
    etiqueta: String
})

const etiqueta = ref(props.etiqueta);
</script>