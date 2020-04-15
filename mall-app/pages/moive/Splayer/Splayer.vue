<template>
	<view>
		<!-- 播放组件 -->
		<view class="">
			player
		</view>
		<web-view
		:src="videoUrl"
		></web-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				videoUrl: ''
			}
		},
		onLoad() {
			var that = this;
			uni.getStorage({
				key: 'video-name',
				success(res){
					that.videoUrl = res.data;
				}
			}),
			uni.removeStorage({
				key: 'video-name',
				success() {
					console.log('success');
				}
			}),
			console.log(this.videoUrl);
		},
		onReady() {
			// #ifdef APP-PLUS
			var currentWebview = this.$mp.page.$getAppWebview();
			currentWebview.setStyle({videoFullscreen: 'auto'})
			// #endif
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
