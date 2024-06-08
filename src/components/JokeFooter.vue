<script setup lang="ts">
import { ref, onUnmounted } from 'vue'

type Joke = {
	setup: string
	punchline: string
}

const joke = ref<Joke>({
	setup: '',
	punchline: '',
})

const visible = ref(false)

const getRandomJoke = async () => {
	try {
		const response = await fetch(
			'https://official-joke-api.appspot.com/jokes/programming/random',
		)
		const data: Joke[] = await response.json()
		joke.value = data[0]
		visible.value = true
		setTimeout(() => {
			visible.value = false
		}, 25000)
	} catch (error) {
		console.error('Error fetching joke:', error)
	}
}

getRandomJoke()

const intervalId = setInterval(getRandomJoke, 60000)

onUnmounted(() => {
	clearInterval(intervalId)
})
</script>

<template>
	<transition name="slide-up">
		<div v-if="visible" class="footer">
			<div class="joke-container">
				<div class="joke">
					<span class="setup">{{ joke.setup }}</span>
					<span class="punchline">{{ joke.punchline }}</span>
				</div>
			</div>
		</div>
	</transition>
</template>

<style lang="scss" scoped>
.footer {
	background-color: #c6d4ca;
	position: fixed;
	bottom: 0;
	left: 0;
	width: 100%;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	transition: transform 0.5s ease-in-out;
}

.slide-up-enter-active,
.slide-up-leave-active {
	transition: transform 0.5s ease-in-out;
}

.slide-up-enter-from,
.slide-up-leave-to {
	transform: translateY(100%);
}

.slide-up-enter-to,
.slide-up-leave-from {
	transform: translateY(0);
}

.joke-container {
	overflow: hidden;
	width: 100%;
	display: flex;
	justify-content: center;
}

.joke {
	display: flex;
	white-space: nowrap;
	animation: slide 25s linear forwards;
	width: 100%;
	justify-content: center;
	align-items: center;
}

.setup,
.punchline {
	display: inline-block;
	padding: 0.2em;
}

@keyframes slide {
	from {
		transform: translateX(100%);
	}
	to {
		transform: translateX(-100%);
	}
}
</style>
