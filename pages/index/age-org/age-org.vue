<template>
	<view class="content">
		<view class="module">
			<view class="left">
				<video src="@/static/video/yuehua.mp4" show-center-play-btn="true"></video>
			</view>
			<view class="right">
				<view class="orgName">
					<text>悦华安养洪武中心</text>
				</view>
				<view class="level">
					<text class="t-icon t-icon-xingxing" v-for="item in 5"></text>
				</view>
				<view class="position">
					<text class="t-icon t-icon-dingwei"></text>
					<text>南京市秦淮区</text>
				</view>
				<view class="classes">
					<text>长者照护之家</text>
					<text>半失能</text>
					<text>失能</text>
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
		}
	}
</script>

<style lang="scss" scoped>
	page{
		display: flex;
		flex-direction: column;
		.content{
			padding: 20rpx;
			.module{
				display: flex;
				flex-direction: row;
				height: 210rpx;
				.left{
					width: 210rpx;
					height: 100%;
					border: 2rpx solid red;
					video{
						width: 100%;
						height: 100%;
					}
				}
				.right{
					width: 500rpx;
					height: 100%;
					padding-left: 20rpx;
					border: 2rpx solid green;
					.orgName{
						color: #282828;
						font-size: 36rpx;
						font-weight: 700;
					}
					.level{
						
					}
					.position{
						font-size: 28rpx;
						color: #333;
					}
					.classes{
						font-size: 28rpx;
						color: #333;
						text{
							border: 2rpx solid rgba(188,188,188,1);
							margin: 0 5rpx;
						}
					}
				}
			}
		}
	}
</style>
