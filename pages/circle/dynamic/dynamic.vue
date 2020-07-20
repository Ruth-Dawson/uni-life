<template>
	<view class="content">
		<view class="sort">
			<button type="default" class="btn" v-for="(item,index) in btns" :key="item.id" :class="btnActive==index?'btnActive':''" :data-current="index" @click="sort">{{item.name}}</button>
		</view>
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
		display: flex;
		.content{
			padding: 0 20rpx;
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
		}
	}
</style>
