<template>
	<view>
		<view class="uni-padding-wrap  uni-common-mt">		
			<view class="uni-flex uni-column">			
				<!-- banner 轮播图 -->
				<view class="uni-flex-item flex-item-V">
						<view class="page-section swiper">
							<view class="page-section-spacing">
								<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration" :circular="circular">
									<swiper-item>
										<view class="swiper-item">
											<image class="bannersize" src="../../../../static/host-banner1.jpg"></image>
										</view>
									</swiper-item>
									<swiper-item>
										<view class="swiper-item">
											<image class="bannersize" src="../../../../static/host-banner2.jpg"></image>
										</view>
									</swiper-item>
									<swiper-item>
										<view class="swiper-item">
											<image class="bannersize" src="../../../../static/host-banner3.jpg"></image>
										</view>
									 </swiper-item>
								</swiper>
							</view>
						</view>
				</view>
				<!-- banner 轮播图 -->
			</view>
			<view class="uni-flex uni-column">	
				<!-- movieserver 操作栏 -->
				<view class="uni-flex-item flex-item-V">
					<view class="uni-flex uni-row row-size">
					    <view class="flex-item uni-bg-red itemleft-size">
							<image class="mov-server-img" src="../../../../static/calendar.png">
								<span class="mov-server-text">看片日历</span>
							</image>
						</view>
					    <view class="flex-item uni-bg-green item-size">
							<image class="mov-server-img" src="../../../../static/rank.png">
								<span class="mov-server-text">电影榜</span>
							</image>
						</view>
					    <view class="flex-item uni-bg-blue itemright-size">
							<image class="mov-server-img" src="../../../../static/resumeplay.png">
								<span class="mov-server-text">继续观看</span>
							</image>
						</view>
					</view>
				</view>
				<!-- movieserver 操作栏 -->
			</view>
			<view class="uni-flex uni-column">	
				<!-- submovie 电影主题 -->
				<view class="uni-flex-item flex-item-V">
					<view class="uni-flex uni-row row-size">
						<view class="flex-item sub-itemleft-size">
							<image class="mov-img-size" src=""></image>
							<span class="mov-text-size">主题片单</span>
						</view>
						<view class="flex-item sub-item-size">
							<image class="mov-img-size" src=""></image>
							<span class="mov-text-size">独家策划</span>
						</view>
						<view class="flex-item sub-itemcenter-size">
							<image class="mov-img-size" src=""></image>
							<span class="mov-text-size">猛男必看</span>
						</view>
						<view class="flex-item sub-item-size">
							<image class="mov-img-size" src=""></image>
							<span class="mov-text-size">免费看</span>	
						</view>
						<view class="flex-item sub-itemright-size">
							<image class="mov-img-size" src=""></image>
							<span class="mov-text-size">找电影</span>	
						</view>
					</view>
				</view>
				<!-- submovie 电影主题 -->
			</view>
		</view>
		<hr class="hr-style"/>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				indicatorDots:true,
				autoplay:true,
				interval:2000,
				duration:500,
				circular:true
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.swiper-item{height: 100%;}
	.bannersize{width: 100%;height: 100%;}
	.itemleft-size{
		width: 30%;
		height: 100rpx;
		margin-left: 3%;
		margin-top: 3%;
		margin-bottom: 3%;
	}
	.item-size{
		width: 30%;
		height: 100rpx;
		margin: 3%;
	}
	.itemright-size{
		width: 30%;
		height: 100rpx;
		margin-right: 3%;
		margin-top: 3%;
		margin-bottom: 3%;
	}
	.mov-server-img{
		width: 56rpx;
		height: 56rpx;
		margin: 20rpx 10rpx;
		display: inline-block;
		float: left;
	}
	.mov-server-text{
		height: 56rpx;
		font-size: 26rpx;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		line-height: 56rpx;
		display: inline-block;
		
	}
	.sub-itemleft-size{
		width: 15%;
		height: 150rpx;
		margin-left: 3%;
	}
	.sub-item-size{
		width: 15%;
		height: 150rpx;
		margin-left: 6%;
		margin-right: 6%;
	}
	.sub-itemright-size{
		width: 15%;
		height: 150rpx;
		margin-right: 3%;
	}
	.sub-itemcenter-size{
		width: 15%;
		height: 150rpx;
	}
	.mov-img-size{
		width: 10%;
		height: 10%;
	}
	.mov-text-size{
		text-align: center;
		font-size: 20rpx;
	}
</style>
