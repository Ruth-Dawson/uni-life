<template>
	<view class="content">
		<!-- 状态栏 -->
		<view class="status_bar"></view>
		<!-- 头部自定义导航栏 -->
		<!-- <uni-nav-bar class="header" :fixed="true" color="#333333" background-color="#F90">
			<block slot="left">
				<view class="city">
					<view><text class="uni-nav-bar-text">{{ city }}</text></view>
					<uni-icons type="arrowdown" color="#333333" size="22" />
				</view>
			</block>
			<view class="input-view">
				<uni-icons class="input-uni-icon" type="search" size="22" color="#666666" />
				<input confirm-type="search" class="nav-bar-input" type="text" placeholder="输入搜索关键词" @confirm="confirm">
			</view>
		</uni-nav-bar> -->
		<!-- 广告轮播 -->
		<view class="advertisement">
			<swiper :indicator-dots="false" :autoplay="true" :interval="3000" :duration="1000" circular="true">
				<swiper-item>
					<view class="swiper-item">
						<image src="/static/img/ad01.png" mode=""></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="/static/img/ad01.png" mode=""></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="/static/img/ad01.png" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<!-- 导航分类 -->
		<view class="nav">
			<view class="nav-container">
				<view class="nav-item" v-for="(item,index) in navItems" :key="index" @click="navigateTo(index)">
					<view class="icon" :style="{backgroundColor:item.backgroundColor}">
						<text class="t-icon" :class="item.iconfont"></text>
					</view>
					<view class="title">
						<text>{{item.title}}</text>
					</view>
				</view>
			</view>
		</view>
		<!-- 推荐轮播 -->
		<view class="wish">
			<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" current="">
				<swiper-item>
					<view class="swiper-item">
						<image src="/static/img/wishbg.png" mode=""></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="/static/img/wishbg.png" mode=""></image>
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<image src="/static/img/wishbg.png" mode=""></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		<!-- 课程报名 -->
		<view class="course">
			<view class="course-container">
				<swiper :indicator-dots="false" :autoplay="true" :interval="3000" :duration="1000" vertical="true" circular="true">
					<swiper-item>
						<view class="swiper-item">
							<view class="left">
								<image src="/static/img/courses01.png" mode=""></image>
							</view>
							<view class="right">
								<view class="title">
									<text>基础版手工制作学习【面授】</text></view>
								<view class="area">
									<text>秦淮区</text>
								</view>
								<view class="time">
									<text>2020.03.27 13：30</text>
									<button type="default">我要报名</button>
								</view>
							</view>
						</view>
					</swiper-item>
					<swiper-item>
						<view class="swiper-item">
							<view class="left">
								<image src="/static/img/courses01.png" mode=""></image>
							</view>
							<view class="right">
								<view class="title">
									<text>基础版手工制作学习【面授】</text></view>
								<view class="area">
									<text>秦淮区</text>
								</view>
								<view class="time">
									<text>2020.03.27 13：30</text>
									<button type="default">我要报名</button>
								</view>
							</view>
						</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
		<!-- 选项卡导航 -->
		<view class="tabs">
			<scroll-view id="tab-bar" class="scroll-h" :scroll-x="true" :show-scrollbar="false" :scroll-into-view="scrollInto">
			    <view v-for="(tab,index) in tabBars" :key="tab.id" class="uni-tab-item" :id="tab.id" :data-current="index" @click="ontabtap">
			        <text class="uni-tab-item-title" :class="tabIndex==index ? 'uni-tab-item-title-active' : ''">{{tab.name}}</text>
			    </view>   <!-- #ifdef APP-PLUS -->
			    
			    <!-- #endif -->
			</scroll-view>
			<view class="line-h"></view>
			<swiper :current="tabIndex" class="swiper-box" :duration="300" @change="ontabchange" :style="{'height':swiperHeight+'px'}">
			    <swiper-item class="swiper-item" id="swiper-item">
			    	<scroll-view class="swiper-item0" scroll-y="true" enable-back-to-top="true" @scrolltolower="loadMore">
						<all></all>
			    	</scroll-view>
			    </swiper-item>
				<swiper-item class="swiper-item " id="swiper-item" >
					<scroll-view scroll-y="true" class="swiper-item1">
						<college></college>
					</scroll-view>
			    </swiper-item>
				<swiper-item class="swiper-item" id="swiper-item">
					<scroll-view scroll-y="true" class="swiper-item2">
						<travel></travel>
					</scroll-view>
				</swiper-item>
				<swiper-item class="swiper-item" id="swiper-item">
					<scroll-view scroll-y="true" class="swiper-item3">
						<job></job>
					</scroll-view>
				</swiper-item>
				<swiper-item class="swiper-item" id="swiper-item">
					<scroll-view scroll-y="true" class="swiper-item4">
						<shop></shop>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue'
	import college from '@/components/uni-sub-index/sub-college.vue'
	import org from '@/components/uni-sub-index/sub-org.vue'
	import job from '@/components/uni-sub-index/sub-job.vue'
	import shop from '@/components/uni-sub-index/sub-shop.vue'
	import travel from '@/components/uni-sub-index/sub-travel.vue'
	import all from '@/components/uni-sub-index/sub-all.vue'
	export default {
		components:{
			uniNavBar,
			college,
			org,
			job,
			shop,
			travel,
			all
		},
		data() {
			return {
				city:"南京",
				navItems:[
					{
						title:'老年大学',
						iconfont:'t-icon-shuben',
						backgroundColor:"#00cccc"
					},
					{
						title:'旅游',
						iconfont:'t-icon-lvyou',
						backgroundColor:"#cccc33"
					},
					{
						title:'愿望清单',
						iconfont:'t-icon-gift',
						backgroundColor:"#ff9999"
					},{
						title:'养老机构',
						iconfont:'t-icon-laoren1',
						backgroundColor:"#ff99cc"
					},
					{
						title:'找工作',
						iconfont:'t-icon-zhifeiji',
						backgroundColor:"#6699ff"
					},
					{
						title:'格子铺',
						iconfont:'t-icon-liwu',
						backgroundColor:"#ffcc66"
					},
					{
						title:'格子铺',
						iconfont:'t-icon-liwu',
						backgroundColor:"#ffcc66"
					},
					{
						title:'格子铺',
						iconfont:'t-icon-liwu',
						backgroundColor:"#ffcc66"
					},
					{
						title:'格子铺',
						iconfont:'t-icon-liwu',
						backgroundColor:"#ffcc66"
					}
				],
				tabBars:[
					{
						id:'all',
						name:'全部'
					},
					{
						id:'oldColleage',
						name:'老年大学'
					},
					{
						id:'travel',
						name:'旅游旅居'
					},
					{
						id:'job',
						name:'找工作'
					},
					{
						id:'shop',
						name:'格子铺'
					}
				],
				scrollInto: "",
				tabIndex: 0,
				newsList: [],
				swiperHeight:1000
			}
		},
		onReady() {
			// 页面初次渲染完成，首先动态加载第一个swiper-iem的对应的sweiper高度
			// 其他的swiper-item点击时更改
			this.getElementHeight('.swiper-item0');
		},
		onLoad() {
			
		},
		onShow() {
		},
		methods: {
			showCity(){
				uni.showToast({
					title: '选择城市'
				})
			},
			scan() {
				uni.showToast({
					title: '扫码'
				})
			},
			confirm() {
				uni.showToast({
					title: '搜索'
				})
			},
			navigateTo(index){
				uni.showToast({
					title:'菜单分类'+index,
					duration:2000
				})
			},
			ontabtap(e){
				let index = e.target.dataset.current || e.currentTarget.dataset.current;
				this.switchTab(index);
				// console.log(e);
				// 点击切换tab的同时，动态改变swiper的高度
				let query=uni.createSelectorQuery().in(this);
				query.exec(function(res){
					// console.log(res);
				})
				// console.log(query.selectAll('#swiper-item')); 
				
			},
			ontabchange(e){
				let index=e.target.current||e.detail.current;
				this.switchTab(index);
			},
			switchTab(index) {
			   this.tabIndex = index;
			   this.scrollInto = this.tabBars[index].id;
			},
			getElementHeight(element){
				setTimeout(()=>{
					let query=uni.createSelectorQuery().in(this);
					query.select(element).boundingClientRect();
					query.exec((res)=>{
						if(!res){
							// 如果没有获取到，再调用一次
							this.getElementHeight();
						}else{
							this.swiperHeight=res[0].height;
							// console.log(res[0].height);
							// console.log(this.swiperHeight);
						}
					})
				},20)
			},
			loadMore(){
				// swiper-item下拉底部加载更多
			}
		}
	}
</script>

<style lang="scss" scoped>
	page {
			display: flex;
			flex-direction: column;
			box-sizing: border-box;
			background-color: #f2f2f2;
			min-height: 100%;
			.content {
				font-size: 14px;
				line-height: 24px;
				background-color: #f2f2f2;
				.header{
					width: 100%;
					top: var(--status-bar-height);
					top: 400rpx;
					// border: 1px solid red;
					.city {
						/* #ifndef APP-PLUS-NVUE */
						display: flex;
						/* #endif */
						flex-direction: row;
						align-items: center;
						justify-content: flex-start;
						/* width: 160rpx;*/
						margin-left: 4px;
					}
					.input-view {
						/* #ifndef APP-PLUS-NVUE */
						display: flex;
						/* #endif */
						flex-direction: row;
						/* width: 500rpx;*/
						flex: 1;
						background-color: #f8f8f8;
						height: 30px;
						border-radius: 15px;
						padding: 0 15px;
						flex-wrap: nowrap;
						margin: 7px 0;
						line-height: 30px;
						.input-uni-icon {
							line-height: 30px;
						}
						.nav-bar-input {
							height: 30px;
							line-height: 30px;
							/* #ifdef APP-PLUS-NVUE */
							width: 370rpx;
							/* #endif */
							padding: 0 5px;
							font-size: 14px;
							background-color: #f8f8f8;
						}
							
					}
				}
				.advertisement{
					margin: 20rpx auto;
					background-color: #f2f2f2;
					height: 200rpx;
					swiper{
						height: 100%;
						.swiper-item{
							display: flex;
							align-items: center;
							justify-content: center;
							position: relative;
							height: 100%;
							background-color: #f2f2f2;
							image{
								height: 100%;
							}
						}
					}
				}
				.nav{
					padding: 0 20rpx;
					background-color: #f2f2f2;
					.nav-container{
						background-color: #fff;
						display: flex;
						flex-wrap: wrap;
						border-radius: 20rpx;
						padding: 20rpx 0;
						.nav-item{
							display: flex;
							flex-direction: column;
							align-items: center;
							box-sizing: border-box;
							width: 142rpx;
							height: 142rpx;
							margin: 10rpx 0;
							.icon{
								border-radius: 50%;
								height: 72%;
								width: 72%;
								background-color: #00cccc;
								display: flex;
								align-items: center;
								justify-content: center;
								.t-icon{
									width: 50%;
									height: 50%;
								}
							}
							.title{
								height: 25%;
							}
						}
					}
				}
				.wish{
					padding: 30rpx 10rpx;
					background-color: #f2f2f2;
					height: 380rpx;
					display: flex;
					align-items: center;
					justify-content: center;
					swiper{
						height: 250rpx;
						width: 100%;
					}
					.swiper-item{
						height: 100%;
						display: flex;
						justify-content: center;
						align-items: center;
						image{
							height: 100%;
						}
					}
				}
				.course{
					width: 100%;
					height: 200rpx;
					padding: 0 20rpx;
					box-sizing: border-box;
					margin-bottom: 20rpx;
					.course-container{
						background-color: #fff;
						border-radius: 20rpx;
						height: 100%;
						box-sizing: border-box;
						swiper{
							height: 100%;
							box-sizing: border-box;
							swiper-item{
								padding: 20rpx;
								box-sizing: border-box;
								.swiper-item{
									display: flex;
									height: 100%;
									.left{
										box-sizing: border-box;
										width: 200rpx;
										image{
											width: 100%;
											height: 100%;
										}
									}
									.right{
										box-sizing: border-box;
										width: 470rpx;
										padding: 0 20rpx;
										.title{
											color: #000;
											font-family: 'Microsoft YaHei';
											font-size: 32rpx;
											margin-bottom: 15rpx;
										}
										.area,.time{
											color: 	#696969;
											font-size: 26rpx;
										}
										.time{
											display: flex;
											justify-content: space-between;
											button{
												width: 150rpx;
												height: 50rpx;
												background-color: #ffcc00;
												color: #000;
												font-size: 26rpx;
												padding: 0;
												display: flex;
												align-items: center;
												justify-content: center;
											}
										}
									}
								}
							}
						}
					}
				}
				.tabs {
				    flex: 1;
				    flex-direction: column;
				    background-color: #ffffff;
				    /* #ifdef MP-ALIPAY || MP-BAIDU */
				    /* #endif */
					.scroll-h {
						width: 750rpx;
						height: 80rpx;
						flex-direction: row;
						// #ifdef APP-PLUS */
						// white-space: nowrap;
						// /* #endif */
						// /* #ifndef APP-PLUS */
						// white-space: nowrap;
						// /* #endif
						white-space: nowrap;
						/* flex-wrap: nowrap; */
						// border-color: #cccccc;
						// border-bottom-style: solid;
						// border-bottom-width: 1px;
						.uni-tab-item {
							// #ifdef APP-PLUS */
							// display: inline-block;
							// /* #endif */
							// /* #ifndef APP-PLUS */
							// display: inline-block;
							// /* #endif
							display: inline-block;
							flex-wrap: nowrap;
							padding-left: 34rpx;
							padding-right: 34rpx;
							.uni-tab-item-title {
								color: #555;
								font-size: 30rpx;
								height: 80rpx;
								line-height: 80rpx;
								flex-wrap: nowrap;
								/* #ifndef APP-PLUS */
								white-space: nowrap;
								/* #endif */
							}
							
							.uni-tab-item-title-active {
								color: #007AFF;
							}
						}
						
					}
					
					.line-h {
						height: 1rpx;
						background-color: #cccccc;
					}
					
					.swiper-box {
						flex: 1;
						display: flex;
						flex-direction: column;
						overflow: scroll;
						.swiper-item {
							flex: 1;
							flex-direction: column;
						}
						
						.scroll-v {
							flex: 1;
							/* #ifndef MP-ALIPAY */
							flex-direction: column;
							/* #endif */
							width: 750rpx;
						}
					}
					
				}
			}
		}
</style>
