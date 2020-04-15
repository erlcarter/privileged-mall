<template>
	<view>
		<view class="uni-padding-wrap  uni-common-mt uni-body">		
			<view class="uni-flex uni-column">			
				<!-- banner 轮播图 -->
				<view class="uni-flex-item flex-item-V">
						<view class="page-section swiper">
							<view class="page-section-spacing">
								<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration" :circular="circular">
									<swiper-item v-for="(item,i) in moviebannerfirst":key="i">
										<view class="swiper-item" @tap="playvideo">
											<image class="bannersize" :src="item.url"></image>
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
				<view class="uni-flex-item flex-item-V centerbannersize1">
					<view id="v-for-banner" class="uni-flex uni-row row-size">
					    <view :class="item.classname" v-for="(item,j) in moviebannersecond":key="j" @tap="openinfo(item.url)">
							<image :src="item.img" class="mov-server-img">
								<span class="mov-server-text">{{item.name}}</span>
							</image>
						</view>
					</view>
				</view>
				<!-- movieserver 操作栏 -->
			</view>
			<view class="uni-flex uni-column">	
				<view class="uni-flex-item centerbannersize2">
					<view class="uni-flex uni-row row-size">
						<view class="flex-item sub-itemleft-size" v-for="(item,k) in moviebannerthrid":key="k">
							<view class="uni-column" @tap="openinfo(item.url)">
								<view class="flex-item item-img">
									<image class="mov-img-size" :src="item.img"></image>
								</view>
							</view>	
							<view class="uni-column">
								<view class="flex-item mov-text-size">
									<span>{{item.name}}</span>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<hr class="hr-style"/>
		<view class="uni-flex uni-column">
			<view class="flex-item">今日推荐</view>
		</view>
		<!-- 推荐电影 -->
		<view class="uni-flex uni-column">
			<view class="flex-item">
				<uni-card>
					<view class="uni-column column-size">
						<view class="flex-item">
							<image class="moive-cover" src="https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2848803552,3617688781&fm=26&gp=0.jpg"></image>
						</view>
					</view>
					<view class="uni-column column-size">
						<view class="flex-item">
							<view class="uni-row">
								<view class="flex-item row-thumbnail-size">
									<image class="moive-thumbnail" src="#" style="height: 50px;" ></image>
								</view>
								<view class="flex-item row-text-size">
									<view class="uni-column">大黄蜂</view>
									<view class="uni-column">2019经典科幻片</view>
								</view>
								<view class="flex-item row-player-size">
									<button>播放</button>
								</view>
							</view>
						</view>
					</view>
				</uni-card>
			</view>
		</view>
	</view>
</template>

<script>	
	import HmRowVideoCard from '@/components/hm-row-video-card/index.vue'
	import uniCard from '@/components/uni-card/uni-card.vue'

	export default {
		components:{
			uniCard
		},
		data() {
			return {
				indicatorDots:true,
				autoplay:true,
				interval:2000,
				duration:500,
				circular:true,
				moviebannerfirst:[
					{url:"../../../static/host-banner1.jpg"},
					{url:"../../../static/host-banner2.jpg"},
					{url:"../../../static/host-banner3.jpg"}
				],
				moviebannersecond:[
					{
						name:"看片日历",
						img:"../../../static/calendar.png",
						url:"../../moive/moivecalandar/moivecalandar",
						classname:"flex-item uni-bg-red itemleft-size"
					},
					{
						name:"电影榜",
						img:"../../../static/rank.png",
						url:"../../moive/moiverank/moiverank",
						classname:"flex-item uni-bg-green itemleft-size"
					},
					{
						name:"继续观看",
						img:"../../../static/resumeplay.png",
						url:"../../moive/moviecontiuneplay/moviecontiuneplay",
						classname:"flex-item uni-bg-blue itemleft-size"
					}
				],
				moviebannerthrid:[
					{
						name:"主题片单",
						img:"../../../static/FilmList.png",
						url:"../../moive/themesheet/themesheet"
					},
					{
						name:"独家策划",
						img:"../../../static/planning.png",
						url:"../../moive/exclusiveplanning/exclusiveplanning"
					},
					{
						name:"高分电影",
						img:"../../../static/HighScoreMovie.png",
						url:"../../moive/highscoremoive/highscoremoive"
					},
					{
						name:"免费看",
						img:"../../../static/free.png",
						url:"../../moive/allmoive/allmoive"
					},
					{
						name:"找电影",
						img:"../../../static/find_movie.png",
						url:"../../moive/findmoive/findmoive"
					}
				]
			}
		},
		methods: {
			openinfo(e) {
			    console.log(e)
			    var navurl = e;    
			    uni.navigateTo({
			        url: navurl,
			         success: res => {},
			        fail: () => {},
			            complete: () => {}
			        });
			    },
				playvideo(e){
				console.log(e)
				var navurl = "../../moive/detail/detail";    
				uni.navigateTo({
				    url: navurl,
				     success: res => {},
				    fail: () => {},
				        complete: () => {}
				    });
			}
		}
	}
</script>

<style>
	body {
	   display: -webkit-box;   /* OLD: Safari,  iOS, Android browser, older WebKit browsers.  */
	   display: -moz-box;      /* OLD: Firefox (buggy) */
	   display: -ms-flexbox;   /* MID: IE 10 */
	   display: -webkit-flex;  /* NEW, Chrome 21–28, Safari 6.1+ */
	   display: flex;          /* NEW: IE11, Chrome 29+, Opera 12.1+, Firefox 22+ */
	 
	   -webkit-box-align: center; -moz-box-align: center; /* OLD… */
	   -ms-flex-align: center; /* You know the drill now… */
	   -webkit-align-items: center;
	   align-items: center;
	 
	   -webkit-box-pack: center; -moz-box-pack: center;
	   -ms-flex-pack: center;
	   -webkit-justify-content: center;
	   justify-content: center;
	 
	   margin: 0;
	   height: 100%;
	   width: 100% /* needed for Firefox */
	}
	
	.uni-body{
		margin-left: 20px;
	}

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
	.centerbannersize1{
		padding-left: 2%;
		padding-right: 2%;
	}
	.centerbannersize2{
		padding-left: 5%;
		padding-right: 5%;
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
		text-align: center;
		display: inline-block;
		
	}
	.sub-itemleft-size{
		width: 15%;
		height: 150rpx;
		margin-left: 13rpx;
		margin-right: 13rpx;
		
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
	.item-img{
		padding-top: 4rpx;
		padding-bottom: 4rpx;
		padding-left: 8rpx;
		padding-right: 8rpx;
		justify-content:space-between;
	}
	.mov-img-size{
		width: 60rpx;
		height: 60rpx;
	}
	.mov-text-size{
		text-align: center;
		font-size: 20rpx;
	}
	.column-size{
		width: 100%;
	}
	.moive-cover{
		width: 100%
	}
	.row-thumbnail-size{
		width: 10%;
		height: 50px;
	}
	.row-text-size{
		width: 70%;
	}
	.row-player-size{
		width: 20%;
	}
</style>
