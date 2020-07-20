<script>
	export default {
		onLaunch: function() {
			console.log('App Launch');
		},
		onShow: function() {
			console.log('App Show');
		},
		onHide: function() {
			console.log('App Hide');
		}
	};
</script>

<style>

@import './static/css/iconfont.css';
/* 彩色图标使用icon-tools生成的iconfont-weapp-icon.css */
@import './static/css/iconfont-weapp-icon.css';

/* 解决头条小程序组件内引入字体不生效的问题 */
/* #ifdef MP-TOUTIAO */
@font-face {
	font-family: uniicons;
	src: url('/static/uni.ttf');
}
/* #endif */


.status_bar{
	height: var(--status-bar-height);
	width: 100%;
	background-color: #FF9900;
	z-index: 9999;
}

</style>
