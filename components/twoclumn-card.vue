<template>
	<view>
		<view class="uni-padding-wrap">
			<view class="title">
				<text>{{ viewObj.title }}</text>
			</view>
			<view class="content">
				<view v-for="(item,index) in viewObj.viewChild" :key="index">
					<text>{{ item.title }}</text>
					<image src="item.centerbgUrl" mode="" />
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "TwoclumnCard",
		props: {
			// viewObj: {
			// 	title: String,
			// 	viewChild: Array,
			// }
		},
		data() {
			return {
				viewObj: {
					title: '英雄分类',
					viewChild: [{
						coverbgUrl: '/static/logo.png',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}]
				}
			}
		},
		methods: {
		}
	}
</script>

<style lang="scss">
	.title {
		margin-top: 40rpx;
		margin-left: 40rpx;
		font-size: 48rpx;
		font-weight: 700;
	}

	.uni-padding-wrap {
		overflow: hidden;
		height: 100%;
		background-color: #FFFFFF;
	}

	.page-section-spacing {
		swiper {
			swiper-item {
				.swiper-item {
					overflow: hidden;
					position: relative;
					width: 506rpx;
					height: 640rpx;
					margin: 68rpx auto;
					box-shadow: 0 10rpx 40rpx #999999;
					border-radius: 40rpx;
					transition: .3s;

					.cover-bg {
						position: absolute;
						top: 0;
						left: 0;
						width: 100%;
						height: 100%;
						z-index: -999;
					}
					
					.center-bg{
						height: 426rpx;
						margin: 40rpx;
						image{
							width: 100%;
							height: 100%;
						}
					}
					
					.head{
						margin-top: 40rpx;
						margin-left: 40rpx;
						.view-title {
							font-size: 36rpx;
							font-weight: 600;
						}
					}
					

					.subtitle {
						color: #999999;
					}

				}

				.swiper-item:active {
					transform: scale(.95);
					transition: .3s;
					box-shadow: 0 10rpx 60rpx #999999;
				}
			}

		}
	}
</style>
