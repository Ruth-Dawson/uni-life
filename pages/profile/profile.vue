<template>
	<view class="root">
		<view class="header u-flex u-row-center u-p-t-75 u-rela">
			<u-image src="/static/img/avatar.png" shape="circle" width="150rpx" height="150rpx" class="avatar" mode="aspectFit"></u-image>
		</view>
		
		<view class="u-m-t-20">
			<u-cell-group>
				<u-cell-item icon="list-dot" title="我的课程"></u-cell-item>
				<u-cell-item icon="star" title="我的收藏"></u-cell-item>
			</u-cell-group>
		</view>
		
		<view class="u-m-t-20">
			<u-cell-group>
				<u-cell-item icon="checkmark-circle" title="实名认证"></u-cell-item>
				<u-cell-item icon="order" title="我的订单"></u-cell-item>
				<u-cell-item icon="map" title="地址管理"></u-cell-item>
				<u-cell-item icon="server-man" title="我的简历"></u-cell-item>
			</u-cell-group>
		</view>
		
		<view class="u-m-t-20">
			<u-cell-group>
				<u-cell-item icon="setting" title="设置"></u-cell-item>
			</u-cell-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				pic:'https://uviewui.com/common/logo.png',
				show:true
			}
		},
		onLoad() {
			
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
page{
	background-color: #ededed;
}

.root{
	.header{
		height: 375rpx;
		background-color: #80809c;
		overflow: hidden;
		&::after{
			content: '';
			width: 1450rpx;
			height: 1450rpx;
			position: absolute;
			bottom: -1320rpx;
			border-radius: 50%;
			background-color: #fff;
			z-index: 1;
		}
		.avatar{
			z-index: 999;
		}
	}
}
</style>
