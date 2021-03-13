<template>
	<view class="">
		<scroll-view scroll-y="true" scroll-top="40px">
			
			
			<show-card v-bind:viewObj="hallViewObj" @goHall="goHall"></show-card>

			<swiper-card @goDetail="goDetail"></swiper-card>

			<twoclumn-card @goDetail="goDetail"></twoclumn-card>

			<view class="bloc"></view>
		</scroll-view>
	</view>
</template>

<script>
	import ShowCard from '../../components/show-card';
	import SwiperCard from '../../components/swiper-card';
	import TwoclumnCard from '../../components/twoclumn-card';

	export default {
		components: {
			ShowCard,
			SwiperCard,
			TwoclumnCard
		},
		data() {
			return {
				hallViewObj: {
					title: '英雄长存',
					subtitle: '快参与到先烈精神的传承中吧～',
					viewChild: [{
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
					}],
				}
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
				let data = {
					
				};
				uni.navigateTo({
					url: '../hall/hall'
				});
			},
			
			goDetail(id) {
				console.log(id);
				uni.navigateTo({
					url: '../detail/detail'
				});
			}
		}
	}
</script>

<style>
	.bloc {
		height: 400px;
	}

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
