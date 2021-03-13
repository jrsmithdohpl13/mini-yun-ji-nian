<template>
	<view>
		<view class="uni-padding-wrap">
			<view class="title">
				<text>{{ viewObj.title }}</text>
			</view>
			<view class="content">
				<view class="card-item"
					v-for="(item,index) in viewObj.viewChild" :key="index"
					@click="onDetail(item.type)" >
					<view class="head">
						<text>{{ item.title }}</text>
					</view>
					<view class="logo">
						<image :src="item.centerbgUrl" />
					</view>
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
						type: 1,
						coverbgUrl: '/static/logo.png',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						type: 2,
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						type: 3,
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}, {
						type: 4,
						coverbgUrl: '',
						centerbgUrl: '/static/icons/shezhi.png',
						title: '民族英雄民族魂',
						subtitle: '百万雄师永不灭'
					}]
				}
			}
		},
		methods: {
			onDetail(typeid) {
				this.$emit('goDetail', {
					id: typeid
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

	.content {
		overflow: hidden;
		height: 100%;
		margin-left: 40rpx;
		padding: 40rpx 0;
		
		.card-item{
			float: left;
			margin-right: 20rpx;
			margin-bottom: 20rpx;
			width: 325rpx;
			height: 400rpx;
			border-radius: 18rpx;
			background-color: #FFFFFF;
			
			.head{
				height: 80rpx;
				margin-top: 20rpx;
				margin-left: 20rpx;
				font-size: 32rpx;
				font-weight: 600;
			}
			
			.logo{
				margin-left: 20rpx;
				width: 285rpx;
				height: 285rpx;
				image{
					width: 100%;
					height: 100%;
				}
			}
		}
		
		.card-item:active {
			transition: .3s;
			background-color: #D0D0D2;
		}
	}
</style>
