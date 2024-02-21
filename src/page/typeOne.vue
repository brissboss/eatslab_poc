<script setup lang="ts">
import { defineProps, onMounted } from 'vue'

const props = defineProps<{
    json: {
        backgroundColor: string,
        textColor: string
    }
}>()

function changeThemeColor() {
    const metaThemeColor = document.querySelector('meta[name=theme-color]');
    if (metaThemeColor) {
        metaThemeColor.setAttribute('content', props.json.textColor);
    }
}

onMounted(() => {
    changeThemeColor();
})

console.log(props.json)

</script>

<template>
    <v-app-bar density="compact">
        <v-tabs
            center-active
            fixed-tabs
            :style="{ width: '100%', backgroundColor: props.json.backgroundColor }"
            :slider-color="props.json.textColor"
        >
            <v-tab
                v-for="index in 4"
                :key="index"
                :value="`test${index}`"
            >
                <div :style="{ color: props.json.textColor }">
                    {{ `test${index}` }}
                </div>
            </v-tab>
        </v-tabs>
    </v-app-bar>
    <v-main
        :style="{ backgroundColor: props.json.backgroundColor, height: '100%', padding: '25px 0'}"
    >
        <v-row>
            <v-col
                v-for="index in 30"
                cols="12"
            >
                <v-card style="margin: 0 15px;">
                    <v-card-title>
                        Lorem ipsum dolor sit.
                    </v-card-title>
                    <v-card-item>
                        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Rerum obcaecati sed labore odit iusto beatae!
                    </v-card-item>
                </v-card>
            </v-col>
        </v-row>
    </v-main>
</template>
