<script setup lang="ts">
import { defineProps, ref, onBeforeMount } from 'vue'

const props = defineProps<{
    partner: string
}>()

const json = ref('')

onBeforeMount(() => {
    fetchJson()
})

function fetchJson() {
    fetch(`https://github.com/brissboss/eatslab_partner/blob/main/${props.partner}.json`)
        .then((response) => response.json())
        .then((data) => {
            console.log(data)
            json.value = JSON.stringify(data)
        })
}

</script>

<template>
    {{ partner + json }}
</template>
