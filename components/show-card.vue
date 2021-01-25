<template>
	<view class="content">
		<image class="cover-bg" :src="viewObj.coverImg" />
		<text class="tag">{{ viewObj.tag }}</text>
		<text class="name">{{ viewObj.name }}</text>
		<text class="introText">{{ viewObj.introText }}</text>
		<text class="deesText">{{ viewObj.deesText }}</text>
		<button @click="toMermryHall" size="mini" type="default">进入纪念馆</button>
	</view>
</template>

<script>
	export default {
		name: 'ShowCard',
		props: {
			viewObj: {
				coverImg: String,
				tag: String,
				name: String,
				introText: String,
				deesText: String,
				color: String
			},
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
	.content{
		position: relative;
		height: 1100rpx;
		border-bottom: 1px #BDBDC2 solid;
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
