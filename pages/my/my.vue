<template>
	<view>
		<text @click="goHome">返回首页</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods: {
			goHome() {
				uni.navigateTo({
					url: '../index/index'
				})
			}
		}
	}
</script>

<style lang="scss">

</style>
