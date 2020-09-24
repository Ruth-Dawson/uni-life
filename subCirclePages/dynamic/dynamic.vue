<template>
	<view class="containerBox">
		<view class="content">
			<view class="sort">
				<button type="default" class="btn" v-for="(item,index) in btns" :key="item.id" :class="btnActive==index?'btnActive':''" :data-current="index" @click="sort">{{item.name}}</button>
			</view>
			<view class="module" v-for="ite in 3">
				<view class="header">
					<view class="left">
						<view class="photo">
							<image src="/static/img/photo.png" mode=""></image>
						</view>
						<view class="name-time">
							<view class="name">
								<text>张奶奶</text>
							</view>
							<view class="time">
								<text space="ensp">今天 13:20</text>
							</view>
						</view>
					</view>
					<view class="right">
						<view class="span">
							<image src="/static/img/dot01.png" mode=""></image>
							<text>旅游</text>
						</view>
						<view class="span">
							<image src="/static/img/dot01.png" mode=""></image>
							<text>摄影</text>
						</view>
					</view>
				</view>
				<view class="container">
					<view class="brief">
						<text>泰国新加坡印度尼西亚 英国俄国美国日本法国只有中国是我最爱的~~</text>
					</view>
					<view class="img">
						<image src="/static/img/circle01.png" mode=""></image>
					</view> 
					<view class="praise-comment">
						<view class="praise">
							<text class="t-icon t-icon-dianzan"></text>
							<text>点赞</text>
						</view>
						<view class="comment">
							<text class="t-icon t-icon-pinglun"></text>
							<text>评论</text>
						</view>
					</view>
					<!-- 点赞及评论模块 有加载，无不加载根据数据来定-->
					<view class="pcContent">
						<view class="praise">
							<view class="left">
								<text class="t-icon t-icon-aixin1"></text>
							</view>
							<view class="right">
								<image src="/static/img/photo01.png" mode="" v-for="item in 15"></image>
								<text>等39人觉得很赞</text>
							</view>
						</view>
						<view class="comment">
							<view class="left">
								<text class="t-icon t-icon-pinglun1"></text>
							</view>
							<view class="right">
								<view class="item" v-for="ie in 5">
									<view class="left-photo">
										<image src="/static/img/photo01.png" mode=""></image>
									</view>
									<view class="right-detail">
										<view class="top">
											<text class="name">雪兰baby</text>
											<text space="ensp" class="time">2月6日 下午1:58</text>
										</view>
										<view class="bottom">
											<text>挺俊、哈哈哈啊哈哈哈哈哈哈哈哈哈挺俊、哈哈哈啊哈哈哈哈哈哈哈哈哈</text>
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<!-- 发布动态按钮  绝对定位 -->
		<!-- <view class="distribute" @click="addDynamic">
				<view class="t-icon t-icon-jiahao2"></view>
		</view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				btns:[
					{
						id:"newest",
						name:"最新"
					},{
						id:"hot",
						name:"热度"
					}
				],
				btnActive:0
			};
		},
		methods:{
			sort(e){
				console.log(e);
				this.btnActive=e.currentTarget.dataset.current||e.target.dataset.current;
				// ajax对接数据加载
			}
		}
	}
</script>

<style lang="scss" scoped>
	page{
		// display: flex;
		.containerBox{
			padding: 0 20rpx;
			background-color: #fff;
			position: relative;
			.distribute{
				border-radius: 50%;
				position: fixed;
				bottom: 30rpx;
				right: 30rpx;
				.t-icon{
					width: 170rpx;
					height: 170rpx;
					z-index: 999;
					border-radius: 50%;
					display: block;
				}
			}
			.content{
				.sort{
					height: 100rpx;
					// justify-content: space-around;
					// align-items: center;
					text-align: center;
					.btn{
						border-radius: 30rpx;
						width: 160rpx;
						height: 60rpx;
						line-height: 60rpx;
						background-color: #f2f2f2;
						color: #333;
						font-size: 30rpx;
						display: inline-block;
						margin: 25rpx;
					}
					.btn::before,
					.btn::after{
						border: 0;
					}
					.btnActive{
						background-color: #f90;
						color: #fff;
					}
				}
				.module{
					margin: 20rpx auto;
					.header{
						height: 100rpx;
						display: flex;
						justify-content: space-between;
						.left{
							display: flex;
							.photo{
								width: 90rpx;
								height: 90rpx;
								border-radius: 50%;
								image{
									width: 100%;
									height: 100%;
								};
							}
							.name-time{
								margin-left: 20rpx;
								.name{
									color: #000;
									font-size: 32rpx;
									height: 50%;
								}
								.time{
									color: #797979;
									font-size: 24rpx;
									height: 50%;
								}
							}
						}
						.right{
							display: flex;
							align-items: center;
							.span{
								display: flex;
								background-color: #f2f2f2;
								border-radius: 20rpx;
								color: #33f;
								font-size: 28rpx;
								padding: 5rpx 8rpx;
								margin: 0 10rpx;
								display: flex;
								align-items: center;
								image{
									width: 16rpx;
									height: 16rpx;
									margin-right: 5rpx;
								}
							}
						}
					}
					.container{
						padding: 20rpx;
						.brief{
							color: #000;
							font-size: 30rpx;
						}
						.img{
							padding: 20rpx 0;
							width:290rpx;
							height: 190rpx;
							image{
								width: 100%;
								height: 100%;
							}
						}
						.praise-comment{
							display: flex;
							height: 50rpx;
							align-items: center;
							color: #333;
							font-size: 28rpx;
							.praise{
								display: flex;
								align-items: center;
								.t-icon{
									font-size: 32rpx;
									margin-right: 10rpx;
								}
								margin-right: 35rpx;
							}
							.comment{
								display: flex;
								align-items: center;
								.t-icon{
									font-size: 32rpx;
									margin-right: 10rpx;
								}
							}
						}
						.pcContent{
							background-color: #f2f2f2;
							.praise{
								border-bottom: 1rpx solid #e8e8e9;
								display: flex;
								padding: 10rpx;
								.left{
									display: flex;
									justify-content: center;
									align-items: flex-start;
									padding: 20rpx 10rpx;
								}
								.right{
									display: flex;
									align-items: center;
									justify-content: flex-start;
									flex-wrap: wrap;
									color: #333333;
									font-size: 24rpx;
									image{
										width: 64rpx;
										height: 64rpx;
										margin: 5rpx;
									}
								}
							}
							.comment{
								display: flex;
								padding: 10rpx;
								.left{
									display: flex;
									justify-content: center;
									align-items: flex-start;
									padding: 30rpx 10rpx;
								}
								.right{
									display: flex;
									flex-grow: 1;
									flex-direction: column;
									.item{
										height: 118rpx;
										display: flex;
										border-bottom: 1rpx solid #e8e8e9;
										padding: 10rpx 10rpx; 
										flex: 1;
										display: flex;
										align-items: center;
										.left-photo{
											display: flex;
											align-items: flex-start;
											justify-content: center;
											align-self: flex-start;
											image{
												width: 64rpx;
												height: 64rpx;
												margin: 10rpx;
											}
										}
										.right-detail{
											flex-grow: 1;
											.top{
												display: flex;
												justify-content: space-between;
												.name{
													color: #445b89;
													font-size: 28rpx;
												}
												.time{
													color:#808081;
													font-size: 24rpx;
												}
											}
											.bottom{
												color: #000;
												font-size: 26rpx;
											}
										}
									}
								}
							}
						}
					}
				}
			}
		}
	}
</style>
