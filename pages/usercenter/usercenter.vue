<template>
	<view>
		<view @click="loginOut" class="">
			退出登陆
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods: {
			// 登出
			loginOut() {
				uni.removeStorage({
				    key: 'openid',
				    success: function (res) {
				        console.log('success');
								uni.reLaunch({
								    url: '../my/my'
								});
				    }
				});
			},
		}
	}
</script>

<style lang="scss">

</style>
