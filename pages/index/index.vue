<template>
	<scroll-view scroll-y="true" scroll-top="40px">
		<view v-for="(item,index) in viewList" :key="index">
			<show-card v-bind:viewObj="item" @goHall = "goHall"></show-card>
		</view>
	</scroll-view>
</template>

<script>
	import ShowCard from '../../components/show-card'
	export default {
		components:{
			ShowCard
		},
		data() {
			return {
				title: 'Hello',
				viewList: [{
					coverImg: '/static/images/lzx.jpeg',
					tag: '民族英雄',
					name: '林则徐',
					introText: '鸦片战争领导者',
					deesText: '1839年，林则徐以钦差大臣赴广东禁烟时，派人明察暗访，强迫外国鸦片商人交出鸦片，并将没收鸦片，于1839年在虎门销毁。',
					color: 'black'
				}, {
					coverImg: '/static/images/lzx.jpeg',
					tag: '民族英雄',
					name: '林则徐',
					introText: '鸦片战争领导者',
					deesText: '1839年，林则徐以钦差大臣赴广东禁烟时，派人明察暗访，强迫外国鸦片商人交出鸦片，并将没收鸦片，于1839年在虎门销毁。',
					color: 'black'
				}]
			}
		},
		onLoad() {
			// this.getOpenid();
		},
		methods: {
			
			// 获取openid
			getOpenid() {
				uni.showLoading({
					mask: true
				});
				uni.login({
					provider: 'weixin',
					success: (loginRes) => {
						uni.hideLoading();
						console.log(loginRes);
					}
				});
			},

			goHall() {
				console.log(11);
				uni.navigateTo({
					url: '../hall/hall'
				});
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
