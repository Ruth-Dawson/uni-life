<template>
	<view class="content" :style="{height:contentH+'px'}" >
			<!-- 瀑布流两列布局 -->
			<view class="listLeft">
				<view class="module" v-for="(item,index) in cardListLeft" :key="item.id" @click="showModule(item.index)">
					<view class="img">
						<image :src="item.url" mode="widthFix" @load="onImageLoad"></image>
					</view>
					<view class="info">
						<view class="brief">
							<text class="brief">{{item.brief}}</text>
						</view>
						<view class="evaluate">
							<text class="t-icon t-icon-xingxing" v-for="(eva,index) in item.evaluate" :key="index"></text>
						</view>
						<view class="price-distance">
							<view class="price">
								<text class="priceNum">￥{{item.price}}</text>
								<text>起</text>
							</view>
							<view class="distance">
								<text class="distanceNum">{{item.distance}}km</text>
							</view>
						</view>
					</view>
					<view class="level">
						<text v-for="(le,index) in item.level" :key="index">A</text>
					</view>
				</view>
			</view>
			<view class="listRight">
				<view class="module"  v-for="(item,index) in cardListRight" :key="item.id" @click="showModule(item.index)">
					<view class="img">
						<image :src="item.url" mode="widthFix"></image>
					</view>
					<view class="info">
						<view class="brief">
							<text class="brief">{{item.brief}}</text>
						</view>
						<view class="evaluate">
							<text class="t-icon t-icon-xingxing" v-for="(eva,index) in item.evaluate" :key="index"></text>
						</view>
						<view class="price-distance">
							<view class="price">
								<text class="priceNum">￥{{item.price}}</text>
								<text>起</text>
							</view>
							<view class="distance">
								<text class="distanceNum">{{item.distance}}km</text>
							</view>
						</view>
					</view>
					<view class="level">
						<text v-for="(le,index) in item.level" :key="index">A</text>
					</view>
				</view>
			</view>
	</view>
</template>

<script>
	export default {
		components:{
		},
		mounted() {
			console.log("mounted加载了");
			this.waterfall();  //初始化瀑布流
		},
		data() {
			return {
				allcardList:[
					{
						url:'/static/img/travel02.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:3,
						level:5,
						price:'29.9',
						distance:'4.5'
					},
					{
						url:'/static/img/travel01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:4,
						level:2,
						price:'39.9',
						distance:'9.0'
					},
					{
						url:'/static/img/course01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:3,
						level:5,
						price:'29.9',
						distance:'4.5'
					},
					{
						url:'/static/img/travel01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:4,
						level:2,
						price:'39.9',
						distance:'9.0'
					},
					{
						url:'/static/img/course01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:3,
						level:5,
						price:'29.9',
						distance:'4.5'
					},
					{
						url:'/static/img/travel01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:4,
						level:2,
						price:'39.9',
						distance:'9.0'
					},
					{
						url:'/static/img/course01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:3,
						level:5,
						price:'29.9',
						distance:'4.5'
					},
					{
						url:'/static/img/travel01.png',
						brief:'谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票谷里薰衣草庄园门票',
						evaluate:4,
						level:2,
						price:'39.9',
						distance:'9.0'
					},
				],
				contentH:800,
				cardListLeft:[],
				cardListRight:[],
				cardLeftHeight:0,
				cardRightHeight:0,
				cardListItem:0,			//作为card的ID
				rImgH:0,				//实际载入的card的高度
				contentH:800,			//设置客户端的屏幕高度默认值
				loadMoreTemp:1,			//作为scoll滚动触底，加载更多的标记，防止多次出发事件，1为允许，0为阻止
				showNoMore:false,		//控制底部“我也是有底线view的显示”
				cardList:null
			};
		},
		methods:{
			onImageLoad(e){
				let divWidth = 345;			//实际显示的单栏宽度，345upx
				let oImgW = e.detail.width; //图片原始宽度
				let oImgH = e.detail.height; //图片原始高度
				let rImgH = divWidth*oImgH/oImgW+170;	//重新计算当前载入的card的高度
				
				if(this.cardListItem==0){
					this.cardLeftHeight += rImgH;	//第一张card高度加到cardLeftHeight
					this.cardListItem++;			//card索引加1
					this.cardListRight.push(this.cardList[this.cardListItem]);	//添加第二张card到cardListRight数组
				}else{
					this.cardListItem++;		//card索引加1
					
						if(this.cardLeftHeight > this.cardRightHeight){		//把card的高度加到目前高度更低的栏中
							this.cardRightHeight += rImgH;		//第二张card高度加到cardRightHeight
						}else{
							this.cardLeftHeight += rImgH;
						}
						
					if(this.cardListItem<this.cardList.length){				//根据目前的栏高，把下一张card，push到低的那栏
						if(this.cardLeftHeight > this.cardRightHeight){
							this.cardListRight.push(this.cardList[this.cardListItem]);		//添加第三张card到cardListRight数组
						}else{
							this.cardListLeft.push(this.cardList[this.cardListItem]);
						}
					}
				}
				
				// console.log(+this.cardListItem);
				if(this.cardListItem%4 == 0){				//每次载入的card数量设置为4，只有载入完成才允许下一次的scroll触底，触发loadMore
					this.loadMoreTemp = 1;
				}
			},
			
			waterfall(){
				console.log("哈哈");
				this.cardList = this.allcardList.slice(0,4);		//初始化图片显示
				console.log(this.cardList);
				this.cardListLeft.push(...this.cardList);			//初始化左侧显示四个
				this.cardListRight.push(...this.cardList);			//初始化左侧显示四个
				console.log(this.cardListLeft);
				this.preLoadImg = this.cardList[0].url;
				var that = this;
				uni.getSystemInfo({		//利用uni-APP获取系统信息Api，获取客户端的屏幕高度，设置成scoll-view的高度，实现触底事件
					success: function (res) {
						that.contentH = res.windowHeight;
					},
				});
			},
			
			loadMore(){
				if(this.loadMoreTemp == 1){			//loadMoreTemp==1,才允许触发
					console.log("loadMore");
					this.loadMoreTemp = 0;			//防止多次触发
					
					let newcardList = this.allcardList.slice(this.cardListItem,this.cardListItem+4);//模拟后端接口返回四个新的数据
					
					//console.log(newcardList);
					if(!newcardList.length == 0){				//判断是否还有新数据
						this.cardList = this.cardList.concat(newcardList);			//返回的新数据加到当前的cardList
						if(this.cardLeftHeight > this.cardRightHeight){				//把第一个新数据加到目前更低的栏上，以触发@load="onImageLoad"
							this.cardListRight.push(newcardList[0]);			
						}else{
							this.cardListLeft.push(newcardList[0]);
						}
					}else{
						this.showNoMore = true;				//没有新数据就显示到底了
					}
				}
			},
			
			showModule(index){
				uni.showToast({
					title: ''+index
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	page{
		display: flex;
		flex-direction: column;
		.content{
			padding: 20rpx;
			display: flex;
			flex-wrap: wrap;
			.listLeft,
			.listRight{
				flex-grow: 1;
				flex-basis: 355rpx;
				box-sizing: border-box;
				flex-shrink: 1;
				.module{
					position: relative;
					display: flex;
					flex-direction: column;
					width: 350rpx;
					padding: 0 10rpx;
					box-sizing: border-box;
					border-radius: 20rpx;
					margin: 12rpx auto;
					.img{
						background-color: #fff;
						image{
							max-width: 100%;
							border-top-right-radius: 20rpx;
							border-top-left-radius: 20rpx;
							min-height: 220rpx;
						}
					}
					.info{
						background-color: #fff;
						padding-left: 15rpx;
						padding-bottom: 15rpx;
						.brief{
							overflow: hidden;
							margin: 8rpx auto;
							text{
								display: -webkit-box;
								-webkit-box-orient:vertical;
								word-break: break-all;
								text-overflow: ellipsis;
								overflow: hidden;
								-webkit-line-clamp: 1;
							}
						}
						.price-distance{
							display: flex;
							justify-content: space-between;
							font-size: 28rpx;
							color: #868686;
							padding-right: 15rpx;
							.price{
								.priceNum{
									font-size: 36rpx;
									color: #f00;
								}
							}
							.distance{
								.distanceNum{
									font-size: 26rpx;
									color: #5e5e5e;
								}
							}
						}
					}
					.level{
						background-color: #f00;
						color: #fff;
						position: absolute;
						left: 10rpx;
						top: 0;
						z-index: 9999;
						border-radius: 15rpx;
						padding: 0 10rpx;
					}
				}
			}
		}
	}
</style>
