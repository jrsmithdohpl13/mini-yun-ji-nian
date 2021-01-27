<template>
	<scroll-view scroll-y="true">
		<view class="user-msg">
			
			<!-- 头像 -->
			<view class="toux">
				<image :src="userInfo.avatarUrl" />
			</view>
			
			<!-- 昵称 微信号 -->
			<view class="wx-name">
				<view class="name">{{ userInfo.nickName }}</view>
				<text class="wx-number">_tanxl</text>
			</view>
			
			<!-- more -->
			<view class="login-btn">
				<button class='authBtn'
					v-if="!isLogin"
					type='primary' 
					open-type='getUserInfo' 
					@getuserinfo='getUserInfo'
					withCredentials="true">授权登录</button>
			</view>	
			<text></text>
		</view>
		
		<!-- 导航条 -->
		<view class="navigation">
			 <view class="">动态</view>
			 <view class="">关注</view>
			 <view class="">场馆</view>
		</view>
	</scroll-view>
</template>

<script>
	export default {
		data() {
			return {
				baseUrl: 'http://localhost:3001',
				isLogin: false,
				userInfo: {
					nickName: '未登录',
					avatarUrl: '../../static/logo.png'
				}
	
			};
		},
		onLoad() {
			// uni.checkSession({
			// 	success: (res) => {
			// 		console.log(res);
			// 	}
			// })
			this.loginStatus();
		},
		methods: {
			loginStatus() {
				var _that = this;
				uni.getStorage({
					key: 'openid',
					success: () => {
						this.isLogin = true;
						uni.getUserInfo({
						  provider: 'weixin',
						  success: function (infoRes) {
						    _that.userInfo.nickName = infoRes.userInfo.nickName;
								_that.userInfo.avatarUrl = infoRes.userInfo.avatarUrl;
						  }
						});
					}
				})
			},
			
			// 用户确认授权后回调
			getUserInfo() {
				var _that = this;
				uni.login({
					provider: 'weixin',
					success: (loginRes) => {
						uni.getUserInfo({
						  provider: 'weixin',
						  success: function (infoRes) {
						    _that.userInfo.nickName = infoRes.userInfo.nickName;
								_that.userInfo.avatarUrl = infoRes.userInfo.avatarUrl;
								_that.isLogin = true;
								
								_that.getOpenid(loginRes.code);
						  }
						});
					},
					fail(err) {
						console.log(err);
					}
				})
			},
			
			// 登出
			loginOut() {
				uni.removeStorage({
				    key: 'oppid',
				    success: function (res) {
				        console.log('success');
								this.isLogin = false;
				    }
				});
			},
			
			// 获取openid
			getOpenid(code) {
				uni.request({
					url: this.baseUrl + '/api/login',
					data: {
						code: code
					},
					success: (res) => {
						console.log(res);
						uni.setStorageSync('openid', res.data.openid);
					},
					fail: (err) => {
						console.log(err);
					}
				})
			},
			
		}
	}
</script>

<style lang="scss">
	.user-msg{
		display: flex;
		align-items: center;
		height: 100%;
		padding: 30rpx 0;
		background-color: #FFFFFF;
		
		.toux{
			display: inline-block;
			width: 160rpx;
			height: 160rpx;
			border-radius: 50%;
			overflow: hidden;
			margin: 20rpx;
			image{
				width: 100%;
				height: 100%;
			}
		}
		
		.wx-name{
			display: inline-block;
			width: 360rpx;
			.name{
				font-size: 36rpx;
				font-weight: bold;
			}
		}
		
		.login-btn{
			button{
				width: 160rpx;
				height: 80rpx;
				text-align: center;
				line-height: 80rpx;
			}
		}
	}

.navigation{
	display: flex;
	width: 100%;
	height: 80rpx;
	margin-top: 10rpx;
	background-color: #FFFFFF;
	view{
		flex: 1;
		display: flex;
		align-items: center;
		justify-content: center;
	}
}
</style>
