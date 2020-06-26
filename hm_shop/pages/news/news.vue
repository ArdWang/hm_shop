<template>
	<view class="news">
		<news-item @itemClick="goDetail" :list="newsList"></news-item>
	</view>
</template>

<script>
	import newsItem from "../../components/news-item/news-item.vue"
	export default {
		components:{
			"news-item":newsItem
		},
		data() {
			return {
				newsList:[]
			}
		},
		onLoad() {
			this.getNews()
		},
		methods: {
			async getNews(){
				const res = await this.$myRequest({
					url:'/api/getnewslist'
				})
				//console.log(res)
				this.newsList = res.data.message
			},
			goDetail(id){
				console.log("gggggggggggg:"+id)
				uni.navigateTo({
					url:"/pages/news-detail/news-detail?id="+id
				})
			}
		}
	}
</script>

<style lang="scss">
	.news{
		.news_item{
			display: flex;
			padding: 10rpx 20rpx;
			border-bottom: 1px solid $shop-color;
			image{
				width: 200rpx;
				min-width: 200rpx;
				max-width: 200rpx;
				height: 150rpx;
			}
			
			.right{
				margin-left: 15rpx;
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				.tit{
					font-size: 30rpx;
				}
				
				.info{
					font-size: 24rpx;
					text:nth-child(2){
						margin-left: 30rpx;
					}
				}
			}
		}
	}
</style>
