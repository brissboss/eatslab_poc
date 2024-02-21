<script setup lang="ts">
import { defineProps, ref, onBeforeMount } from 'vue'
import TypeOne from './typeOne.vue'
import testJson from './nomad.json'

const props = defineProps<{
    partner: string
}>()

const json = ref<any>(null)
const loading = ref<boolean>(true)

onBeforeMount(async () => {
    const test = await fetch(`https://eatslab-partner.vercel.app/${props.partner}.json`)
    const data = await test.json()
    json.value = data
    loading.value = false
})


</script>

<template>
    <TypeOne v-if="!loading && testJson.type === 1" :json="testJson"/>
</template>
