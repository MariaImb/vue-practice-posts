<script setup>

const emit = defineEmits(['next', 'prev'])

defineProps(["inicio", "fin", "maxLength"]);

</script>

<template>
    <div class="mb-2">
        <v-btn @click="emit('prev')" variant="outlined" :disabled="inicio <= 0"> Previus</v-btn>
        <v-btn  @click="emit('next')" variant="outlined" :disabled="fin >= maxLength"> Next </v-btn>
    </div>
</template>
