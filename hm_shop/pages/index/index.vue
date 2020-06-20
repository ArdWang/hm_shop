<template>
	<view class="home">
		<swiper indicator-dots circular>
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.img">	
			</swiper-item>
		</swiper>
		<!--导航区域-->
		<view class="nav">
			<view class="nav_item">
				<view class="iconfont icon-ziyuan">	
				</view>
				<text>黑马超市</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-guanyuwomen">	
				</view>
				<text>联系我们</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-tupian">	
				</view>
				<text>社区图片</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-shipin">	
				</view>
				<text>学习视频</text>
			</view>
		</view>
		<!--推荐商品区域-->
		<view class="hot_goods">
			<view class="tit">推荐商品</view>
			<view class="goods_list">
				<view class="goods_item" v-for="item in goods" :key="item.id">
					<image :src="item.img_url"></image>
					<view class="price">
						<text>￥{{item.sell_price}}</text>
						<text>￥{{item.market_price}}</text>
					</view>
					<view class="name">
						{{item.title}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers:[],
				goods:[]
			}
		},
		onLoad() {
			this.getSwipers()
			this.getHotGoods()
		},
		methods: {
			//获取轮播图的数据
			async getSwipers(){
				const res = await this.$myRequest({
					url:'/api/getlunbo'
				})
				this.swipers = res.data.message
			},
			
			//获取热门列表数据
			async getHotGoods(){
				const res = await this.$myRequest({
					url:'/api/getgoods?pageindex=1'
				})
				this.goods = res.data.message
			}
		}
	}
</script>

<style lang="scss">
	.home{
		swiper{
			width: 750rpx;
			height: 380rpx;
			image{
				height: 100%;
				width: 100%;
			}
		}
		
		.nav{
			display: flex;
			.nav_item{
				width: 25%;
				text-align: center;
				view{
					width: 120rpx;
					height: 120rpx;
					background: $shop-color;
					border-radius: 60rpx;
					margin: 10px auto;
					line-height: 120rpx;
					color: #fff;
					font-size: 50rpx;
				}
				
				.icon-tupian{
					font-size: 45rpx;
				}
				
				text{
					font-size: 30rpx;
				}
			}
		}
		.hot_goods{
			background: #EEE;
			overflow: hidden;
			margin-top: 10px;
			.tit{
				height: 50px;
				line-height: 50px;
				color: $shop-color;
				text-align: center;
				letter-spacing: 20rpx;
				background: #FFF;
				margin: 7rpx 0;
			}
			.goods_list{
				padding: 0 15rpx;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				.goods_item{
					background: #FFF;
					width: 355rpx;
					margin: 10rpx 0;
					padding: 15rpx;
					box-sizing: border-box;
					image{
						width: 80%;
						height: 150px;
						display: block;
						margin: auto;
					}
					.price{
						margin: 20rpx 0 5rpx 0;
						color: $shop-color;
						font-size: 36rpx;
						text:nth-child(2){
							color: #CCC;
							font-size: 28rpx;
							margin-left: 17rpx;
							text-decoration: line-through;
						}
					}
					.name{
						font-size: 28rpx;
						line-height: 50rpx;
						padding-bottom: 15rpx;
						padding-top: 10rpx;
					}
				}
			}
		}
	}
</style>
