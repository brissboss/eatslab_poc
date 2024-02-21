<script setup lang="ts">
import RouterPage from '@/page/RouterPage.vue'

const partner = window.location.href.split('/')[window.location.href.split('/').length - 1]

</script>

<template>
	<v-app>
		<v-main>
			  <RouterPage
            :partner="partner"
        />
		</v-main>
	</v-app>
</template>
