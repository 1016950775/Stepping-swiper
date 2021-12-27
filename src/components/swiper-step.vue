<template>
	<div id="window" :style="{'width': `${swiperWidth}px`,'height': `${swiperHeight}px`}">
		<div class="box" :style="{'marginLeft':`${marginLeft}px`,'transition': transition}">
			<div class="img" id="div" :style="{'marginRight':`${spacing}px`}" v-for="(item,index) in data1"
				@mouseover="suspend" @mouseleave="start">
				<img :style="{'width':`${imgWidth}px`}" :src="item.num">
				<span>{{item.id}}</span>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'swiperStep',
		props: {
			data: {
				type: Array,
				default: () => []
			},
			imgNum: {
				type: Number,
				default: 4
			},
			swiperHeight: {
				type: Number,
				default: 150
			},
			spacing: {
				type: Number,
				default: 10
			},
			imgWidth: {
				type: Number,
				default: 190
			},
			interval: {
				type: Number,
				default: 3000
			}

		},
		data() {
			return {
				maxMarginLeft: 200,
				index: 0,
				marginLeft: 0,
				swiperWidth: 500,
				setinterval: null,
				data1: [],
				transition: `margin-left 1s`
			};
		},
		methods: {
			start() {
				this.setinterval = setInterval(this.moveChange, this.interval)
			},

			moveChange() {
				this.transition = `margin-left 1s`
				this.index++
				console.log(this.index)
				let marginLeft = this.index * (this.imgWidth + this.spacing)
				this.marginLeft = -marginLeft
				console.log(this.marginLeft, marginLeft)
				if (marginLeft == this.maxMarginLeft) {
					setTimeout(() => {
						this.transition = 'none'
						this.index = 0
						this.marginLeft = 0
					}, 1000)
				}
			},

			suspend() {
				clearInterval(this.setinterval);
			},
		},
		mounted() {
			console.log(this.data, '拿到的数据')

			this.data1 = this.data.concat(this.data)

			this.maxMarginLeft = (this.imgWidth + this.spacing) * this.data.length
			console.log(this.maxMarginLeft, "最大的margin值")
			this.swiperWidth = this.imgWidth * this.imgNum + (this.imgNum - 1) * this.spacing


			this.start()
		}
	}
</script>

<style scoped>
	#window {
		border: 1px solid red;
		overflow: hidden;
	}

	.box {
		width: 100%;
		height: 100%;
		display: flex;
	}

	.img {
		background-color: #0000FF;
		font-size: 20px;
		text-align: center;
		color: #FFFFFF;
		position: relative;
		cursor: pointer;
	}

	img {
		/* width: 190px; */
		height: 100%;
	}

	span {
		position: absolute;
		left: 20px;
		color: #FFFFFF;
	}
</style>
