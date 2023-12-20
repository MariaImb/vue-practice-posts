<script setup>

const emit = defineEmits(['next', 'prev'])
</script>

<template>
    <div class="mb-2">
        <v-btn @click="emit('prev')" variant="outlined"> Previus </v-btn>
        <v-btn  @click="emit('next')" variant="outlined"> Next </v-btn>
    </div>
</template>
