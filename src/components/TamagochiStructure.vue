<script setup lang="ts">
import { ref, computed } from 'vue'
import TamagochiButton from '@/components/TamagochiButton.vue'
import TamagochiScreen from '@/components/TamagochiScreen.vue'

const textList = ref([] as string[])

const computedKey = computed(() => textList.value.join(' '))

const updateText = (newTextList: string[]) => {
	textList.value = newTextList
}
</script>
<template>
	<div class="tamagochi">
		<div class="screen"></div>
		<TamagochiScreen :key="computedKey" :text-list="textList"> </TamagochiScreen>
		<div class="btn-luck">
			<TamagochiButton
				:text-list="['FEELING LUCKY?']"
				variant="feeling-lucky"
				@update-text="updateText"
			></TamagochiButton>
		</div>
		<div class="btn-about">
			<TamagochiButton
				:text-list="['ABOUT', 'ME']"
				variant="about-me"
				@update-text="updateText"
			></TamagochiButton>
		</div>
		<div class="btn-tour">
			<TamagochiButton
				:text-list="['TAKE A TOUR', '(PROJECTS)']"
				variant="projects-tour"
				@update-text="updateText"
			></TamagochiButton>
		</div>
	</div>
</template>

<style scoped lang="scss">
.tamagochi {
	position: absolute;
	display: inline-table;
	background-image: url('@/assets/imgs/tamagochi.svg');
	background-size: cover;
	background-repeat: no-repeat;
	bottom: 4rem;
}
.screen {
	position: absolute;
	top: 41.25%;
	left: 50%;
	width: 29%;
	height: 23.55%;
	border-radius: 12%;
	transform: translate(-50%, 0);
}
.btn-luck {
	position: absolute;
	bottom: 17%;
	left: 35%;
}
.btn-about {
	position: absolute;
	bottom: 11%;
	left: 50%;
	transform: translate(-50%, 0%);
}
.btn-tour {
	position: absolute;
	bottom: 17%;
	right: 35%;
}
</style>
