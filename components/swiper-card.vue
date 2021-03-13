<template>
	<view>
		<view class="uni-padding-wrap">
			<view class="title">
				<text>{{ viewObj.title }}</text>
			</view>
			<view class="page-section">
				<view class="page-section-spacing">
					<swiper class="swiper" style="height: 400px;" previous-margin="100rpx" next-margin="100rpx">
						<swiper-item v-for="(item, index) in viewObj.viewChild" v-bind:key="index" style="overflow: visible;">
							<view class="swiper-item"
								@click="onDetail(item.storyid)">
								<image class="cover-bg" :src="item.coverbgUrl"
								 v-if="(item.coverbgUrl&&!item.centerbgUrl) || (item.coverbgUrl&&item.centerbgUrl)"/>
								<view class="head">
									<view class="view-title">{{ item.title }}</view>
									<text class="subtitle">{{ item.subtitle }}</text>
								</view>
								<view class="center-bg">
									<image v-if="!item.coverbgUrl&&item.centerbgUrl" :src="item.centerbgUrl" />
								</view>
							</view>
						</swiper-item>
					</swiper>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "SwiperCard",
		props: {
			// viewObj: {
			// 	title: String,
			// 	viewChild: Array,
			// }
		},
		data() {
			return {
				viewObj: {
					title: '英雄故事',
					viewChild: [{
						storyid: 1,
						coverbgUrl: '/static/logo.png',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						storyid: 2,
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						storyid: 3,
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}]
				}
			}
		},
		methods: {
			onDetail(id) {
				this.$emit('goDetail', {
					id: id
				});
			}
			
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
