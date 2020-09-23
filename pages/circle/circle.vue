<template>
	<view class="content">
		<!-- 导航占位符 -->
		<view class="status_bar"></view>
		<view class="nav navbar">
			<view class="navItem">
				<navigator url="/pages/circle/circle">圈子</navigator>
			</view>
			<view class="navItem">
				<navigator url="/pages/index/index">首页</navigator>
			</view>
			<view class="navItem">
				<navigator url="/pages/counsel/counsel">咨讯</navigator>
			</view>
		</view>
		<!-- <uni-nav-bar class="navbar" leftIcon="back" leftText="返回" rightText="菜单" title="圈子" @clickLeft="back"></uni-nav-bar> -->
		<view class="tabs">
			<scroll-view scroll-x="true" id="tab-bar" :show-scrollbar="false">
				<view v-for="(tab,index) in tabBars" :key="tab.id" class="uni-tab-item" id="tab.id" :data-current="index" @click="ontabtap">
					<text class="uni-tab-item-title" :class="tabIndex==index?'uni-tab-item-title-active':''">{{tab.name}}</text>
				</view>
			</scroll-view>
			<!-- 由于在swiper组件中position:fixed;会失效，所以在动态页面中无法实现 悬浮 添加按钮   -->
			<!-- 当swiper滑动到动态页面时，再显示该按钮 -->
			<view class="distribute" style="position: fixed;bottom: 30rpx;right: 30rpx;z-index: 9999;opacity: 0.7;" v-show="showAddDynamic">
				<navigator url="/pages/circle/dynamic/addDynamic/addDynamic">
					<view class="t-icon t-icon-jiahao2" style="width: 150rpx;height: 150rpx;"></view>
				</navigator>
			</view>
			<swiper :indicator-dots="false" :autoplay="false" :interval="3000" :duration="1000" :current="tabIndex" @change="ontabchange">
				<swiper-item>
					<view class="swiper-item">
						<dynamic></dynamic>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<u-video></u-video>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<topic></topic>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<talk></talk>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<friend></friend>
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
	import dynamic from "@/pages/circle/dynamic/dynamic.vue"
	import talk from "@/pages/circle/talk/talk.vue"
	import topic from "@/pages/circle/topic/topic.vue"
	import uVideo from "@/pages/circle/uVideo/uVideo.vue"
	import friend from "@/pages/circle/friend/friend.vue"
	export default {
		components:{
			uniNavBar,
			dynamic,
			talk,
			topic,
			uVideo,
			friend
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
				],
				showAddDynamic:true
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
				if(index==0){
					this.showAddDynamic=true;
				}else{
					this.showAddDynamic=false;
				}
			},
			switchTab(index){
				this.tabIndex=index;
			},
			back(){
				uni.navigateBack({
					delta:1
				})
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
					height: 2700rpx;
				}
			}
		}
	}
</style>
