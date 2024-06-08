<script setup lang="ts">
type Props = {
	textList: string[]
}
const { textList } = defineProps<Props>()
</script>

<template>
	<div class="screen">
		<span v-for="(text, i) in textList" :key="i"> {{ text }}<br /> </span>
	</div>
</template>

<style scoped lang="scss">
.screen {
	background-color: rgba(0, 0, 0, 0.2);
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	overflow: hidden;
	position: relative;

	animation: blink-shadow 1s forwards;

	&:after {
		content: '';
		position: absolute;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0);
		animation: blink 1s forwards;
	}

	@keyframes blink {
		0%,
		100% {
			background-color: rgba(0, 0, 0, 0);
		}
		1% {
			background-color: rgba(255, 255, 255, 0.2);
		}
		2% {
			background-color: rgba(136, 129, 32, 0.4);
		}
	}
	@keyframes blink-shadow {
		0%,
		100% {
			box-shadow: rgba(136, 129, 32) 0 0 0 0;
		}
		1% {
			box-shadow: rgb(255, 248, 157) 0 0 30px 0;
		}
		2% {
		}
	}
}
span {
	color: #e0b658;
	justify-content: center;
	text-align: center;
	align-items: center;
	max-width: 90%;
	font-size: large;
	animation: move 1.1s ease-in-out forwards;
	transform: translateZ(20%);
	text-shadow: 0 0.2em 0.3em rgba(0, 0, 0, 0.5);
	letter-spacing: -0.1em;
	line-height: 1.2;
}

@keyframes move {
	0% {
		transform: scale(0.8) translateY(-1em) translateZ(2em);
		opacity: 0;
	}
	50% {
		transform: scale(1.1) translateZ(2em);
		opacity: 0.5;
	}
	75% {
		transform: scale(1) translateY(1%) translateZ(2em);
		opacity: 1;
	}
	100% {
		transform: scale(1) translateY(1%) translateZ(2em);
		opacity: 1;
	}
}
</style>
