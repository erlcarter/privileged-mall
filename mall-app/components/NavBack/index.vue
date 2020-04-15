<template name="NavBack">
	<view class="navback bg-gradual-blue">
		<text class="back-icon text-gray cuIcon-back" @tap="goBack"></text>
	</view>
</template>

<script>
	export default {
		name:"NavBack",
		props:{},
		methods:{
			goBack(){
				history.back();
			}
		}
	}
</script>

<style>
	@import url('./index.css');
</style>
