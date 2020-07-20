<template>
	<view class="content">
			<view class="left">
				左
			</view>
			<view class="right">
				右
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
	.content{
		display: flex;
		flex-wrap: wrap;
		.left,
		.right{
			flex-basis: 360rpx;
			border: 2rpx solid red;
		}
	}
</style>
