<template>
	<view class="content">
		<!-- 导航占位符 -->
		<view class="status_bar"></view>
		<uni-nav-bar leftIcon="back" leftText="返回" rightText="菜单" title="圈子"></uni-nav-bar>
		<view class="tabs">
			<scroll-view scroll-x="true" id="tab-bar" :show-scrollbar="false">
				<view v-for="(tab,index) in tabBars" :key="tab.id" class="uni-tab-item" id="tab.id" :data-current="index" @click="ontabtap">
					<text class="uni-tab-item-title" :class="tabIndex==index?'uni-tab-item-title-active':''">{{tab.name}}</text>
				</view>
			</scroll-view>
			<swiper :indicator-dots="false" :autoplay="false" :interval="3000" :duration="1000" :current="tabIndex" @change="ontabchange">
				<swiper-item>
					<view class="swiper-item">
						<dynamic></dynamic>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						2
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						3
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						4
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						5
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
	import dynamic from "@/pages/circle/dynamic/dynamic"
	export default {
		components:{
			uniNavBar,
			dynamic
		},
		data() {
			return {
				tabIndex:0,
				tabBars:[
					{
						id:"dynamic",
						name:"动态"
					},{
						id:"video",
						name:"小视频"
					},{
						id:"topic",
						name:"话题"
					},{
						id:"whipser",
						name:"悄悄话"
					},{
						id:"bosom-friend",
						name:"寻知音"
					}
				]
			};
		},
		methods:{
			ontabtap(e){
				let index=e.currentTarget.dataset.current||e.target.dataset.current;
				this.switchTab(index);
			},
			ontabchange(e){
				let index=e.detail.current||e.target.current;
				this.switchTab(index);
			},
			switchTab(index){
				this.tabIndex=index;
			}
		}
	}
</script>

<style lang="scss" scoped>
	page{
		display: flex;
		flex-direction: column;
		.content{
			.tabs{
				flex: 1;
				#tab-bar{
					display: flex;
					flex-direction: row;
					white-space: nowrap;
					background-color: #f2f2f2;
					color: #333;
					font-size: 32rpx;
					height: 150rpx;
					width: 750rpx;
					align-items: center;
					.uni-tab-item{
						display: inline-block;
						align-self: center;
						width: 20%;
						line-height: 150rpx;
						// width: 150rpx;
						// height: 100rpx;
						box-sizing: border-box;
						text-align: center;
						.uni-tab-item-title{
							position: relative;
						}
						.uni-tab-item-title-active{
							font-size: 36rpx;
							color: #000;
							font-weight: 700;
						}
						.uni-tab-item-title-active::after{
							width: 50%;
							height: 8rpx;
							content: " ";
							background-color: #f90;
							position: absolute;
							bottom: -20rpx;
							left: 50%;
							transform: translateX(-50%);
						}
					}
				}
				swiper{
					border: 1px solid red;
				}
			}
		}
	}
</style>
