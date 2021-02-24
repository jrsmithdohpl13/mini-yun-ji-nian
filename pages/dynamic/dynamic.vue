<template>
	
	<scroll-view scroll-y="true" >
		<view v-for="(item,index) in contriList" :key="index">
			<contribution-card v-bind:comtriObj="item" @goContri="goContribution()"></contribution-card>
		</view>
	</scroll-view>
	<!-- 	<view>
			<van-tabs
			 v-model="active"
			 color="#99999"
			 title-active-color="#1890FF">
			  <van-tab title="标签 1">内容 1</van-tab>
			  <van-tab title="标签 2">内容 2</van-tab>
			  <van-tab title="标签 3">内容 3</van-tab>
			  <van-tab title="标签 4">内容 4</van-tab>
			</van-tabs>
		</view> -->
</template>

<script>
	import ContributionCard from '../../components/contribution-card';
	export default {
		components: {
			ContributionCard
		},
		data() {
			return {
				active: 2,
				contriList: [{
					title: '打响新冠防疫战1',
					subtitle: '一只小白兔',
					intro: '截至1月25日09时，全国累计报告确诊病例100136例，现有确诊病例2828例，境外输入4611例；海外现有确诊病例27508353例。',
					videoUrl: 'https://stream7.iqilu.com/10339/upload_transcode/202002/18/20200218114723HDu3hhxqIT.mp4'
				}, {
					title: '打响新冠防疫战2',
					subtitle: '一只小白兔',
					intro: '截至1月25日09时，全国累计报告确诊病例100136例，现有确诊病例2828例，境外输入4611例；海外现有确诊病例27508353例。',
					videoUrl: 'https://stream7.iqilu.com/10339/upload_transcode/202002/18/20200218093206z8V1JuPlpe.mp4'
				}, {
					title: '打响新冠防疫战3',
					subtitle: '一只小白兔',
					intro: '截至1月25日09时，全国累计报告确诊病例100136例，现有确诊病例2828例，境外输入4611例；海外现有确诊病例27508353例。',
					videoUrl: 'https://stream7.iqilu.com/10339/article/202002/18/2fca1c77730e54c7b500573c2437003f.mp4'
				}, {
					title: '打响新冠防疫战4',
					subtitle: '一只小白兔',
					intro: '截至1月25日09时，全国累计报告确诊病例100136例，现有确诊病例2828例，境外输入4611例；海外现有确诊病例27508353例。',
					videoUrl: 'https://stream7.iqilu.com/10339/upload_transcode/202002/18/20200218025702PSiVKDB5ap.mp4'
				}]
				
			};
		},
		methods: {
			onChange(event) {
			    uni.showToast({
			      title: `切换到标签 ${event.detail.name}`,
			    });
			  },
				
			goContribution() {
				uni.navigateTo({
					url: '../contribution/contribution'
				})
			}
		}
	}
</script>

<style lang="scss">

</style>
