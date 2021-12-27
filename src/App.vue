<template>
	<div id="app">
		<img alt="Vue logo" src="./assets/logo.png">
		<!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
		<h1 style="text-align: left;">步进轮播</h1>
		<swiperStep :data="swiperData" :imgNum="imgNum"></swiperStep>
	</div>
</template>

<script>
	// import HelloWorld from './components/HelloWorld.vue'
	import swiperStep from '@/components/swiper-step.vue'

	export default {
		name: 'app',
		components: {
			// HelloWorld
			swiperStep
		},
		data() {
			return {
				imgNum:3,
				swiperData: [{
					id: 0,
					num: '../assets/logo.png'
				}, {
					id: 1,
					num: '../assets/c1.png'
				}, {
					id: 2,
					num: '../assets/c2.png'
				}, {
					id: 3,
					num: '../assets/c3.png'
				}, {
					id: 4,
					num: '../assets/c4.png'
				}, {
					id: 5,
					num: '../assets/c5.png'
				}, {
					id: 6,
					num: '../assets/c6.png'
				}, {
					id: 7,
					num: '../assets/c7.png'
				}, {
					id: 8,
					num: '../assets/c8.png'
				}, {
					id: 9,
					num: '../assets/c9.png'
				}]
			}
		},
		created() {

		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
