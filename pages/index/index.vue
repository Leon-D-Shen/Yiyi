<template>
	<view class="container">
		
		<text class="intro">首页</text>

		<tab-bar :data='app_nav' @currentPageChange='currentPageChange'></tab-bar>
	</view>
</template>

<script>
	import TabBar from '../../components/tabBar'
	import { baseURL } from '../../common/utils/config'
	export default {
		components: {
			TabBar
		},
		data() {
			return {
				pageKey:'上课',
				app_nav: {
					nav_list:[
						{
							title:'上课',
							url:baseURL+'/static/icon/shangke.png',
							active_url:baseURL+'/static/icon/shangke-active.png',
							page_key:'上课'
						},
						{
							title:'发现',
							url:baseURL+'/static/icon/faxian.png',
							active_url:baseURL+'/static/icon/faxian-active.png',
							page_key:'发现'
						},
						{
							title:'我的',
							url:baseURL+'/static/icon/wode.png',
							active_url:baseURL+'/static/icon/wode-active.png',
							page_key:'我的'
						}
					]
				},
			}
		},
		methods: {
			// 底部导航栏切换
			currentPageChange(e) {
				this.current_page = e.page_key
				if (e.page_key != 'home') {
					uni.setNavigationBarTitle({
						title: e.text,
					});
				} else {
					uni.setNavigationBarTitle({
						title: e.text,
					});
				}
				if (e.page_key == "classify") {
					uni.setNavigationBarColor({
						frontColor: '#000000',
						backgroundColor: "#ffffff"
					});
				} else {
					uni.setNavigationBarColor({
						frontColor: this.app_nav.top_color,
						backgroundColor: this.app_nav.top_background
					});
				}
			},

		}
	}
</script>

<style>
/* 	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	} */
</style>
