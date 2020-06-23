<template>
	<view class="contact">
		<image class="img" src="http://www.itcast.cn/2018czydz/images/gywmban.jpg"></image>
		<view class="info">
			<view @click="phone">联系电话：18928357301(点击拨打电话)</view>
			<view>联系地址: 惠州市惠城区</view>
		</view>
		<map class="map" :longitude="longitude" :scale="scale" :latitude="latitude" :markers="markers"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				longitude:114.418978,
				latitude:23.138876,
				scale:13,
				markers:[
					{
						longitude:114.418978,
						latitude:23.138876,
						iconPath:'../../static/hmlogo.png',
						width:30,
						height:30
					}
				]
			}
		},
		methods: {
			phone(){
				uni.makePhoneCall({
					phoneNumber:'18928357301'
				})
			}
		}
	}
</script>

<style lang="scss">
	.contact{
		.img{
			width: 750rpx;
			height: 320rpx;
		}
		
		.info{
			padding: 10rpx 20rpx;
			font-size: 30rpx;
			view{
				line-height: 80rpx;
				border-bottom: 1px #eee solid;
			}
			
		}
		
		.map{
			width: 750rpx;
			height: 750rpx;
		}
		
	}
</style>
