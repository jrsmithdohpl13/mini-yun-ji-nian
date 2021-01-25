<template>
	<view class="content">
		<view class="header">
			
			<view class="author-msg">
				<image src="../static/logo.png" />
				<view class="text-title">
					<view class="title">{{ comtriObj.title }}</view>
					<text class="sub-title">{{ comtriObj.subtitle }}·投稿了视频</text>
				</view>
			</view>
			<view class="more-control">
				<view class="more">
					<image src="../static/icons/more.png" />
				</view>
			</view>
		</view>
			
		<view class="video-player">
			<video
				:src="comtriObj.videoUrl"
				controls>
			</video>
			<text class="video-intro">{{ comtriObj.intro }}</text>
		</view>
		
		<view class="nav-bottom">
			<!-- 点赞 -->
			<view class="thumbs-up">
				<image src="../static/icons/dianzan.png" />
				<!-- <image src="../static/icons/dianzan_2_active.png" /> -->
			</view>
			
			<!-- 评论 -->
			<view class="comment">
				<image @click="toContribution()" src="../static/icons/chat.png" />
			</view>
			
			<!-- 转发 -->
			<view class="forward">
				<image src="../static/icons/zhuanfa.png" />
				<text style="margin-left: 10rpx;">转发</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'ContributionCard',
		props: {
			comtriObj: {
				title: String,
				subtitle: String,
				intro: String,
				videoUrl: String
			}
		},
		data() {
			return {
				
			};
		},
		methods: {
			toContribution() {
				this.$emit('goContri');
			}
		}
	}
</script>

<style lang="scss">
.content{
	overflow: hidden;
	margin-top: 20rpx;
	height: 100%;
	background-color: #FFFFFF;
}
	
.header{
	display: flex;
	margin: 20rpx;
	height: 80rpx;
	.author-msg{
		flex: 2;
		image{
			margin-right: 20rpx;
			width: 60rpx;
			height: 60rpx;
		}
		.text-title{
			display: flex;
			align-items: center;
			height: 30rpx;
			display: inline-block;
			line-height: 1;
			.title{
				font-size:32rpx;
			}
			.sub-title{
				margin-top: 1rpx;
				font-size: 24rpx;
				color: #999999;
			}
		}
	}
	.more-control{
		flex: 1;
		display: flex;
		justify-content: flex-end;
		.more{
			width: 40rpx;
			height: 40rpx;
			image{
			width: 100%;
			height: 100%;
		}
		}
	}
}

.video-player{
	margin: 20rpx 0;
	video{
		width: 100%;
	}
	.video-intro{
		margin: 0 10rpx;
		font-weight: 600;
		word-break: break-all;
		text-overflow: ellipsis;
		overflow: hidden;
		display: -webkit-box;
		-webkit-line-clamp: 1;
		-webkit-box-orient: vertical;
	}
}

.nav-bottom{
	display: flex;
	align-items: center;
	width: 100%;
	height: 80rpx;
	font-size: 24rpx;
	color: #999999;
	
	image{
		width: 40rpx;
		height: 40rpx;
	}
	view{
		flex: 1;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.thumbs-up{
	}
	
	.comment{
	}
	
	.forward{
	}
}
</style>
