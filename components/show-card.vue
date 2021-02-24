<template>
	<view class="wrap">
		<view class="head">
			<view class="title">
				<text>{{ viewObj.title }}</text>
			</view>
			<text class="subtitle">{{ viewObj.subtitle }}</text>
		</view>
		<view class="content"
				v-for="(item, index) in viewObj.viewChild" v-bind:key="index" >
			<image class="cover-bg" :src="item.coverImg" />
			<text class="tag">{{ item.tag }}</text>
			<text class="name">{{ item.name }}</text>
			<text class="introText">{{ item.introText }}</text>
			<text class="deesText">{{ item.deesText }}</text>
			<button @click="toMermryHall" size="mini" type="default">进入纪念馆</button>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'ShowCard',
		props: {
			viewObj: {
				title: String,
				subtitle: String,
				viewChild: Array
			}
		},
		data() {
			return {
			};
		},
		onLoad() {
			
		},
		methods: {
			toMermryHall() {
				this.$emit('goHall');
			}
		}
		
	}
</script>

<style lang="scss">
	.wrap{
		background-color: #FFFFFF;
	}
	
	.head{
		overflow: hidden;
		.title{
			margin: 10rpx 40rpx;
			font-size: 48rpx;
			font-weight: 700;
			box-shadow: 0 1rpx 1rpx #999999;
		}
		
		.subtitle{
			display: inline-block;
			height: 40rpx;
			margin-left: 40rpx;
			font-size: 24rpx;
			line-height: 24rpx;
			color: #999999;
		}
		
	}
	
	.content{
		position: relative;
		height: 1100rpx;
		box-shadow: 0 1rpx 1rpx #BDBDC2;
		.cover-bg{
			width: 100%;
			height: 100%;
		}
		.tag{
			position: absolute;
			top: 20rpx;
			left: 20rpx;
			color: #8E8E92;
		}
		.name{
			position: absolute;
			top: 60rpx;
			left: 20rpx;
			color: #FFFFFF;
			font-size: 32px;
			font-weight: 600;
		}
		.introText{
			position: absolute;
			top: 150rpx;
			left: 20rpx;
			color: #FFFFFF;
		}
		.deesText{
			position: absolute;
			left: 20px;
			bottom: 20px;
			width: 220px;
			height: 45px;
			color: #FFFFFF;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			-webkit-line-clamp: 2;
			overflow: hidden;
		}
		button{
			position: absolute;
			bottom: 20px;
			right: 20px;
			border-radius: 20px;
			color: #3478F6;
			font-weight: bold;
		}
	}
</style>
