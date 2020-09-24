<template>
	<view class="content">
		<view class="module" v-for="(item,index) in 5" @click="apply(index)">
			<view class="name">
				<view class="left">
					<text class="position">养老护理员</text>
					<text class="type">兼职</text>
				</view>
				<view class="right">
					<text>3k-6k</text>
				</view>
			</view>
			<view class="address-time">
				<view class="address">
					<text space="ensp">南京市 | 秦淮区</text>
				</view>
				<view class="time">
					<text>2020.03.26</text>
				</view>
			</view>
			<view class="request">
				<text class="">55岁以内</text>
				<text>女性</text>
				<text>细心</text>
			</view>
			<view class="company">
				<view class="left">
					<text>江苏悦华养老产业集团</text>
				</view>
				<view class="right">
					<button type="default" @click="apply(index)">申请</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			apply(index){
				uni.showToast({
					title: '申请'+index
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	page{
		display: flex;
		flex-direction: column;
		position: relative;
		.content{
			background-color: #f2f2f2;
			padding: 20rpx;
			.module{
				background-color: #fff;
				width: 100%;
				height: 290rpx;
				padding: 30rpx;
				box-sizing: border-box;
				border-radius: 20rpx;
				margin-bottom: 30rpx;
				.name{
					display: flex;
					justify-content: space-between;
					.left{
						display: flex;
						.position{
							color: #363636;
							font-size: 34rpx;
							margin-right: 15rpx;
						}
						.type{
							color: #f00;
							font-size: 24rpx;
							padding: 0 15rpx;
							background-color: rgba(255, 204, 102, 0.51);
							border-radius: 15rpx;
							box-sizing: border-box;
						}
					}
					.right{
						color: #f30;
						font-size: 28rpx;
					}
				}
				.address-time{
					display: flex;
					justify-content: space-between;
					margin: 15rpx 0;
					.address{
						color: #797979;
						font-size: 28rpx;
					}
					.time{
						color: #333;
						font-size: 26rpx;
					}
				}
				.request{
					margin: 15rpx 0;
					text{
						font-size: 24rpx;
						background-color: #f2f2f2;
						color: #333;
						padding: 0 15rpx;
						margin-right: 10rpx;
					}
				}
				.company{
					display: flex;
					justify-content: space-between;
					text{
						color: #000;
						font-size: 28rpx;
					}
					button{
						background-color: rgba(255, 153, 153, 0.356862745098039);
						color: #f00;
						font-size: 26rpx;
						border-radius: 30rpx;
						width: 110rpx;
						height: 60rpx;
						display: flex;
						align-items: center;
						margin: 0;
					}
					button::after{
						border: 0;
					}
				}
			}
		}
	}
</style>
