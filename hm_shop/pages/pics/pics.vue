<template>
	<view class="pics">
		<scroll-view class="left" scroll-y>
			<view class="active">家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	page{
		height: 100%;
	}
	.pics{
		height: 100%;
		.left{
			width: 200rpx;
			height: 100%;
			border-right: 1px solid #eee;
			view{
				height: 60px;
				line-height: 60px;
				color: #333;
				text-align: center;
				font-size: 30rpx;
				border-top: 1px solid #eee;
			}
			.active{
				background: $shop-color;
				color: #FFF;
			}
		}
		
	}
</style>
