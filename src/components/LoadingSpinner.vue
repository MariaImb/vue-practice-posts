<template>
    <div class="loading-container">
        <v-progress-circular color="primary" model-value="20" :size="60" indeterminate></v-progress-circular>
    <p>Loading...</p>
    </div>

</template>

<style>
.loading-container {
   display: flex;
   flex-direction: column;
   align-items: center;
   justify-content: center;
}
</style>