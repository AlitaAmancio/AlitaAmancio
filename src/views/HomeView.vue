<script setup lang="ts">
import JokeFooter from '@/components/JokeFooter.vue'
import TamagochiStructure from '@/components/TamagochiStructure.vue'
</script>

<template>
	<div class="wrapper">
		<div style="flex-grow: 1; display: flex; justify-content: center">
			<h1>
				<span> ALITA </span>
				<br />
				<span> AMANCIO </span>
			</h1>
			<TamagochiStructure></TamagochiStructure>
			<JokeFooter />
		</div>
	</div>
</template>

<style scoped lang="scss">
.wrapper {
	position: relative;
	min-width: 100%;
	min-height: 100vh;
	display: flex;
	justify-content: center;
}
.tamagochi {
	position: absolute;
	display: inline-table;
	background-image: url('@/assets/imgs/tamagochi.svg');
	background-size: contain;
	background-repeat: no-repeat;
	width: 26rem;
	height: 26rem;
	bottom: 3.5rem;
}
h1 {
	position: absolute;
	top: 6%;
	color: #c6d4ca;
	text-shadow: 0 0.09em 0.2em rgba(0, 0, 0, 0.5);
	letter-spacing: -0.05em;
	line-height: 0.8;
	justify-content: center;
	text-align: center;
	align-items: center;
	font-size: 6rem;
}
</style>
