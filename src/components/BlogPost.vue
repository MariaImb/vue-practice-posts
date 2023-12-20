<script setup>
const props = defineProps({
    title: String,
    body: {
        type: String,
        default: "sin descripciones"
    },
    id: Number
}

)

</script>

<template>
    <v-card class="mb-3" max-width="100%" variant="outlined">
        <v-card-item>
            <div>
                <div class="text-overline mb-1"></div>
                <div class="text-h6 mb-1">
                    {{ id }} - {{ title }}
                </div>
                <div class="text-caption">{{ body }}</div>
            </div>
        </v-card-item>

        <v-card-actions>
            <v-btn> Button </v-btn>
        </v-card-actions>
    </v-card>
</template>
