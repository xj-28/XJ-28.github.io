<template>
	<view class="">
		<view class="container" v-if="!isShow">
			<view class="sha">
				<image src="../../static/goin.png" @click="show" mode="aspectFit"></image>
			</view>
		</view>
		<view id="contents" v-if="isShow">
		</view>
	</view>

</template>

<script>
	const mp3 = require('./mp3.mp3')
	export default {
		data() {
			return {
				isShow: false,
				showMyOrExample: false,
			}
		},
		onLoad(opt) {
		},
		mounted() {

		},
		methods: {
			show() {
				this.isShow = true
				const innerAudioContext = uni.createInnerAudioContext();
				innerAudioContext.autoplay = true;
				innerAudioContext.src = mp3
				innerAudioContext.onPlay(() => {
				  console.log('开始播放');
				});
				setTimeout(() => {
					this.start();
				}, 1000);
				require('./script.js')
			},
			start() {
				const text = [
					"十月四号是个神奇的一天，让我遇到了你",
					"1004这日子，又如同两个人（00）的一生一世（14）",
					"或许这就是巧合，亦或许是命中注定",
					"让我在对的时间遇到对的你",
					"你的出现让我明白了什么是爱情",
					"你的性格如绿叶般清新，你的笑容如花朵般绽放",
					"你的一举一动都让我为之倾倒",
					"我想对你说，我愿意用一生的时间去呵护你，陪你走过风雨，共享阳光",
					"一起走过今年，明年，直至永远",
					"所以...... xxxxx",
					"可以做我未来的那个她吗？",
					"----- BY xxxx"
				]
				const text2 = [
					"-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx-xxxxxxx",
					"-xxxxxxx",
					"-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx-xxxxxxx-xxxxxxx-xxxxxxx",
					"-xxxxxxx",
					"-xxxxxxx？",
					"-xxxxxxx"
				]
				let str = text.join('<br><br>')
				let str_ = ''
				let i = 0
				let content = document.getElementById('contents')
				let timer = setInterval(() => {
					if (str_.length < str.length) {
						str_ += str[i++]
						content.innerHTML = '<p>' + str_ +
							'<span class="xx" style="opacity: 1; color: red;">&nbsp;&nbsp;💞</span></p>' //打印时加光标
					} else {
						clearInterval(timer)
						content.innerHTML = '<p>' + str_ + '</p>'
					}
				}, 100)
			}
		}
	}
</script>

<style>
	.audio {
		position: fixed;
		z-index: 20;
	}
	#contents {
		position: fixed;
		z-index: 10;
		width: 90%;
		left: 5%;
		top: 20vh;
		padding: 10px;
		filter: drop-shadow(rgba(0,0,0,.3) 5px 5px 0);
		-webkit-backdrop-filter: blur(8px);
		backdrop-filter: blur(2px);
		border-radius: 25px;
		box-shadow:inset 0 0 6px rgba(255, 255, 255, 0.2);
		color: #fff;
		font-weight: 600;
		display: flex;
		padding-top: 30rpx;
	}
	.container {
		height: 100vh;
		background-image: url('../../static/bg2.png');
		background-size: 100% 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.sha {
		height: 100vh;
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		-webkit-backdrop-filter: blur(4px);
		backdrop-filter: blur(2px);
		box-shadow:inset 0 0 6px rgba(255, 255, 255, 0.2);
	}
	.container image {
		width: 40%;
	}
</style>