<template>
	<scroll-view scroll-y="true">
		<view></view>
	</scroll-view>
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
