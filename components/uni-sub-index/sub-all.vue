<template>
	<view class="content">
		<view class="module" v-for="item in listItems" :key="item.id" @click="moduleContent(item.name)">
			<view class="top" :style="{background:'url('+item.image+')',backgroundRepeat:'no-repeat',backgroundSize:'100% 100%'}">
				
			</view>
			<view class="bottom">
				<view class="name">
					<text>{{item.name}}</text>
				</view>
				<view class="brief">
					<text :style="{color:item.fontColor}">{{item.brief}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		onLoad() {
			console.log("全部页加载了");
		},
		data() {
			return {
				listItems:[
					{
						id:'colleage',
						image:'/static/img/oldCo01.png',
						name:'老年大学',
						brief:'"带你走进不一样的课堂"',
						fontColor:'#f30'
					},
					{
						id:'travel',
						image:'/static/img/oldCo05.png',
						name:'旅游 旅居',
						brief:'"带你走进不一样的课堂"',
						fontColor:'#c3c'
					},
					{
						id:'wish',
						image:'/static/img/oldCo05.png',
						name:'愿望清单',
						brief:'"带你走进不一样的课堂"',
						fontColor:'#c3c'
					},
					{
						id:'oldOrg',
						image:'/static/img/oldCo05.png',
						name:'养老机构',
						brief:'"带你走进不一样的课堂"',
						fontColor:'#c3c'
					},
					{
						id:'job',
						image:'/static/img/oldCo05.png',
						name:'找工作',
						brief:'"带你走进不一样的课堂"',
						fontColor:'#c3c'
					},
					{
						id:'shop',
						image:'/static/img/oldCo05.png',
						name:'格子铺',
						brief:'"带你走进不一样的课堂"',
						fontColor:'#c3c'
					}
				],
			};
		},
		methods:{
			moduleContent(name){
				uni.showToast({
					title:name+'模块'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content{
		padding: 0 20rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		background-color: #f2f2f2;
		.module{
			height: 440rpx;
			width: 710rpx;
			margin-top: 40rpx;
			background-color: #fff;
			border-top-right-radius: 15rpx;
			border-top-left-radius: 15rpx;
			.top{
				height: 270rpx;
				width: 100%;
			}
			.bottom{
				height: 170rpx;
				width: 100%;
				display: flex;
				flex-direction: column;
				.name{
					color: #5e5e5e;
					font-size: 34rpx;
					font-weight: 700;
					flex:1;
					display: flex;
					align-items: center;
					padding-left: 20rpx;
				}
				.brief{
					flex: 1;
					font-size: 32rpx;
					padding-left: 40rpx;
				}
			}
		}
	}
	image{
		width: 700rpx;
		height: 100rpx;
	}
</style>
