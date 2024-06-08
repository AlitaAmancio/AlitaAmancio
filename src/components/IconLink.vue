<script setup lang="ts">
import { defineProps } from 'vue'

type Props = {
	icon: string
	url: string
}

const { icon, url } = defineProps<Props>()
</script>

<template>
	<a :href="url" target="_blank" class="icon-link">
		<div class="icon-wrapper">
			<img :src="icon" alt="Icon" class="icon-image" />
		</div>
	</a>
</template>

<style scoped lang="scss">
.icon-link {
	display: inline-block;
	width: 2em;
	height: 2em;
	background-color: #c47e71;
	border-radius: 30%;
	overflow: hidden;
	text-align: center;
	transition: background-color 0.3s;
	position: relative;
	margin: 0.5em;

	&:hover {
		background-color: #684039;
	}
}

.icon-wrapper {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	pointer-events: none;
	justify-content: center;
	align-items: center;
}

.icon-image {
	width: 90%;
	height: 90%;
}
</style>
