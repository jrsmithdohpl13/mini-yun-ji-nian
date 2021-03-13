<template>
	<view class="dynamic">
		<view class="dynamic_tab">
			<view class="dynamic_tab_title">
				<uni-segmented-control :current="current" :values="items.map(v=>v.title)" @clickItem="onClickItem" styleType="text"
				 style="border: none;"></uni-segmented-control>
			</view>
			<view class="dynamic_tab_content">
				<scroll-view scroll-y="true">
					<view v-if="current === 0">
						<view v-for="(item,index) in items[0].contriList" :key="index">
							<contribution-card 
								v-bind:comtriObj="item" 
								@goContri="goContribution()"
								@click="goDetail()"
								></contribution-card>
						</view>
					</view>
					<view v-if="current === 1">
						选项卡2的内容
					</view>
				</scroll-view>
			</view>
		</view>

	</view>
</template>

<script>
	import {
		uniSegmentedControl
	} from "@dcloudio/uni-ui";

	import ContributionCard from '../../components/contribution-card';
	export default {
		components: {
			ContributionCard,
			uniSegmentedControl
		},
		data() {
			return {
				items: [{
						title: '视频',
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
					},
					{
						title: '综合'
					},

				],
				current: 0,
			};
		},
		methods: {
			onClickItem(e) {
				if (this.current !== e.currentIndex) {
					this.current = e.currentIndex;
				}
			},
			
			goDetail() {
				uni.navigateTo({
					url: '../detail/detail'
				})
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
	.dynamic_tab {
		background-color: #FFFFFF;
		.dynamic_tab_title {
			width: 60%;
			margin: 0 auto;
		}
	}
</style>
