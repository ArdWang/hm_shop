<template>
	<view class="goods_list">
		<goods-list :goods="goods"></goods-list>
	</view>
</template>

<script>
	import goodsList from '../../components/goods-list/goods-list.vue'
	export default {
		
		data() {
			return {
				pageindex:1,
				goods:[]
			}
		},
		components:{
			"goods-list": goodsList
		},
		onLoad() {
			this.getGoodsList()
		},
		methods: {
			//获取商品列表得数据
			async getGoodsList(){
				const res = await this.$myRequest({
					url: '/api/getgoods?pageindex='+this.pageindex
				})
				this.goods = res.data.message
			}
		}
	}
</script>

<style lang="scss">
	.goods_list{
		background: #eee;
	}
</style>
