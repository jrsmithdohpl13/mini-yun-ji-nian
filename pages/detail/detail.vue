<template>
	<view>

		<scroll-view scroll-y="true">
			<view class="video_player">
				<video
					autoplay="true"
					src="https://stream7.iqilu.com/10339/article/202002/18/2fca1c77730e54c7b500573c2437003f.mp4" 
					controls
				></video>
			</view>

			<view class="content">
				<view class="nav_line">
					<view class="tab_btn">
						<uni-segmented-control
							:current="current"
							:values="items.map(v=>v.title)"
							@clickItem="onClickItem"
							styleType="text"
							style="border: none;"
							active-color="pink"
						></uni-segmented-control>
					</view>
				</view>
				<view class="tab_warp">
					<view v-if="current === 0">
						<view class="uesrMsg">
							<!-- 头像 关注按钮 -->
							<view class="top-line">
								<view class="toux">
									<image src="../../static/logo.png" />
								</view>
								
								<view class="intro-text">
									<view class="">
										<text>Re酒歌</text>
									</view>
									<text>100w关注</text>
								
								</view>
								<view class="follow">
									+ 关注
								</view>
								
								<!--  -->
								<view class="">
									
								</view>
							</view>
							
							
						</view>
					</view>
					<view v-if="current === 1">
						选项卡2的内容
					</view>
				</view>
			</view>
		</scroll-view>
		<!-- <nav-bar></nav-bar> -->

	</view>
</template>

<script>
	import {
		uniSegmentedControl
	} from "@dcloudio/uni-ui";
	import NavBar from "../../components/nav-bar.vue";
	export default {
		components: {
			NavBar,
			uniSegmentedControl
		},
		data() {
			return {
				items: [{
					title: '简介'
				}, {
					title: '祝福语'
				}],
				current: 0,
			};
		},
		methods: {
			onClickItem(e) {
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex;
				}
			},
		}
	}
</script>

<style scoped lang="scss">
	.video_player{
		overflow: hidden;
		width: 100%;
		height: 400rpx;
		video{
			width: 100%;
			height: 100%;
		}
	}
	
	.content{
		.nav_line{
			background-color: #FFFFFF;
			.tab_btn{
				width: 30%;
				margin-left: 40rpx;
				
				/deep/ .segmented-control__item{
					margin-left: 40rpx;
				}
				
				/deep/ .segmented-control__text{
					// color: #999999 !important;
					font-size: 24rpx;
				}
			}
		}
		.tab_warp{
			overflow: hidden;
			height: 800px;
			background-color: #FFFFFF;
			.uesrMsg{
				margin-top: 40rpx;
				.top-line{
					display: flex;
					align-items: center;
					margin-left: 40rpx;
					.toux{
						overflow: hidden;
						width: 100rpx;
						height: 100rpx;
						border-radius: 50%;
						image{
							width: 100%;
							height: 100%;
						}
					}
					.intro-text{
						margin-left: 20rpx;
						font-size: 24rpx;
					}
					.follow{
						display: flex;
						width: 140rpx;
						height: 60rpx;
						margin-left: 300rpx;
						line-height: 60rpx;
						color: #FFFFFF;
						background-color: pink;
						border-radius: 10rpx;
						justify-content: center;
					}
				}
			}
		}
	}
</style>
