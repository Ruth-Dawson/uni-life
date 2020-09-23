<template>
	<view class="content">
		<uni-nav-bar class="navbar" leftIcon="back" leftText="返回" @clickLeft="back"></uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue'
	
	export default {
		components:{
			uniNavBar
		},
		data() {
			return {
				
			};
		},
		methods:{
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
			background-color: #f2f2f2;
		}
	}
</style>
