<script>
	export default {
		onLaunch: function() {
			console.log('App Launch');
			// #ifdef APP-PLUS
			plus.screen.lockOrientation('portrait-primary'); //锁定竖屏正方向
			// #endif
		},
		onShow: function() {
			console.log('App Show');
		},
		onHide: function() {
			console.log('App Hide');
		},
		globalData:{
			userName:'白居易'
		}
	};
</script>

<style lang="scss">
//引入uView基础样式 
@import "uview-ui/index.scss";

// @import "https://at.alicdn.com/t/font_1841210_61dmzue8ag9.css";

@import 'static/css/iconfont.css';


@import "./static/css/iconfont-weapp-icon.css";
// 彩色图标使用icon-tools生成的iconfont-weapp-icon.css

.status_bar{
	height: var(--status-bar-height);
	width: 100%;
	background-color: #FF9900;
	z-index: 9999;
}

/* 顶部导航 固定再顶部 */
.navbar{
	position: fixed;
	top: 0;
	left: 0;
	right: 0;
}

.nav{
	display: flex;
	justify-content: center;
	.navItem{
		
	}
}


</style>
