<script setup lang="ts">
import { defineProps, computed } from 'vue'

type Props = {
	variant: string
	textList: string[]
}

const { variant, textList } = defineProps<Props>()

const computedClass = computed(() => {
	return `btn btn-${variant}`
})
</script>

<template>
	<button
		:class="computedClass"
		@click="$emit('click')"
		@mouseover="$emit('updateText', textList)"
		@mouseleave="$emit('updateText', [])"
	></button>
</template>

<style lang="scss" scoped>
.btn {
	padding: 1em 1em;
	border: none;
	cursor: pointer;
	font-size: 1em;
	border-radius: 50%;
	position: relative;
	transition:
		background-color 0.6s,
		background-image 0.6s;

	&.btn-feeling-lucky {
		background-color: #ba7165;

		&:hover {
			background-color: #ffe078;
			animation: bounce-in 0.6s forwards;
		}
	}

	&.btn-projects-tour {
		background-color: #9e4d46;

		&:hover {
			background-color: #ffe078;
			animation: bounce-in 0.6s forwards;
		}
	}

	&.btn-about-me {
		background-color: #ac5f56;

		&:hover {
			background-color: #ffe078;
			animation: bounce-in 0.6s forwards;
		}
	}

	@keyframes bounce-in {
		0% {
			transform: scale(1.1);
		}
		50% {
			transform: scale(0.9);
		}
		100% {
			transform: scale(1.1);
		}
	}
}
</style>
