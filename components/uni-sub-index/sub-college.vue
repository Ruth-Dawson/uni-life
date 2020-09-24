<template>
	<view class="content">
		<view class="module" v-for="(item,index) in courses" :key="index" @click="showModule">
			<view class="img">
				<image :src="item.url" mode=""></image>
			</view>
			<view class="module-container">
				<view class="title">
					<text>{{item.title}}</text>
				</view>
				<view class="praise-price">
					<view class="praiseContent">
						<text class="t-icon t-icon-dianzan"></text>
						<text class="praiseNum">{{item.praiseNum}}</text>
					</view>
					<text class="price" v-if="item.price==0">免费</text>
					<text class="price" v-else>￥{{item.price}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				courses:[
					{
						title:'课程名称',
						url:'/static/img/course01.png',
						praiseNum:99,
						price:0
					},
					{
						title:'课程名称',
						url:'/static/img/course01.png',
						praiseNum:99,
						price:39.9
					},
					{
						title:'课程名称',
						url:'/static/img/course01.png',
						praiseNum:99,
						price:99.9
					},
					{
						title:'课程名称',
						url:'/static/img/course01.png',
						praiseNum:99,
						price:0
					},
					{
						title:'课程名称',
						url:'/static/img/course01.png',
						praiseNum:99,
						price:9.9
					}
				]
			};
		},
		methods:{
			showModule(){
				uni.showToast({
					title: '课程模块'
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content{
		padding: 20rpx 10rpx;
		display: flex;
		flex-wrap: wrap;
		background-color: #f2f2f2;
		.module{
			width: 365rpx;
			height: 380rpx;
			padding: 0 15rpx;
			box-sizing: border-box;
			margin-bottom: 20rpx;
			.img{
				height: 250rpx;
				width: 100%;
				background-color: #fff;
				border-top-left-radius: 15rpx;
				border-top-right-radius: 15rpx;
				image{
					max-width: 100%;
					height: 100%;
				}
			}
			.module-container{
				background-color: #fff;
			}
			.title{
				font-size: 32rpx;
				color: #000;
				height: 70rpx;
				display: flex;
				align-items: center;
				padding-left: 20rpx;
			}
			.praise-price{
				display: flex;
				justify-content: space-between;
				height: 60rpx;
				padding:0 20rpx;
				.praise{
					font: 28rpx;
					color: #949494;
				}
				.praiseContent{
					display: flex;
					align-items: center;
					.t-icon{
						width: 44rpx;
						height: 44rpx;
						margin-right: 10rpx;
						color: red;
					}
					.praiseNum{
						color: #949494;
						font-size: 28rpx;
					}
				}
				.price{
					display: flex;
					align-items: center;
					font-size: 30rpx;
					color: #f00;
				}
			}
		}
	}
</style>
