<template>
	<view class="goods_list">
		<goods-list @goodsItemClick="getgoodsDetail" :goods="goods"></goods-list>
		<view class="isOver" v-if="flag">......我是有底线得......</view>
	</view>
</template>

<script>
	import goodsList from '../../components/goods-list/goods-list.vue'
	export default {
		
		data() {
			return {
				pageindex:1,
				goods:[],
				flag:false
			}
		},
		components:{
			"goods-list": goodsList
		},
		onLoad() {
			this.getGoodsList()
		},
		onPullDownRefresh() {
			console.log("下拉刷新了")
			this.pageindex = 1
			this.goods = []
			this.flag = false
			
			setTimeout(()=>{
				this.getGoodsList(()=>{
					uni.stopPullDownRefresh()
				})
			},1000)
		},
		onReachBottom() {
			console.log(this.goods.length)
			if(this.goods.length<this.pageindex*10) return this.flag = true
			console.log("触底了")
			this.pageindex++
			this.getGoodsList()
		},
		methods: {
			//获取商品列表得数据
			async getGoodsList(callBack){
				const res = await this.$myRequest({
					url: '/api/getgoods?pageindex='+this.pageindex
				})
				this.goods = [...this.goods, ...res.data.message]
				callBack && callBack()
			},
			
			//跳转到导航商品详情页面
			getgoodsDetail(id){
				uni.navigateTo({
					url:'/pages/goods-detail/goods-detail?id='+id
				})
			}
			
		}
	}
</script>

<style lang="scss">
	.goods_list{
		background: #eee;
	}
	.isOver{
		width: 100%;
		height: 50px;
		line-height: 50px;
		text-align: center;
		font-size: 28rpx;
	}
	
</style>
