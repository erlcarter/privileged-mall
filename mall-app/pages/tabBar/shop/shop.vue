<template>
	<view>
		
		<view class="uni-padding-wrap uni-common-mt" style="margin-bottom: 10rpx;margin-left: 20px;">
			<!-- 搜索 -->
			<view class="uni-flex uni-column">
				<view class="uni-flex-item flex-item-V">
					<uni-search-bar :radius="100" @confirm="search"></uni-search-bar>
				</view>
			</view>

			<!-- 商品类目 -->
			<view class="uni-flex uni-column">
				<view class="uni-flex-item flex-item-V">
					<view class="uni-flex uni-row">
						<view class="flex-item item-size" v-for="(item,i) in shopbannerFirst":key="i">
							<view class="uni-column img-div">						
								<image class="shop-item-size  item-img" :src="item.img" @tap="openinfo(item.url)"></image>					
							</view>
							<view>
								<view class="flex-item shop-text-align">
								<span class="shop-item-text">{{item.name}}</span>
								</view>
							</view>
						</view>
					</view>
					<view class="uni-flex uni-row">
						<view class="flex-item item-size" v-for="(item,j) in shopbannerSecond":key="j">
							<view class="uni-column img-div">						
								<image class="shop-item-size  item-img" :src="item.img" @tap="openinfo(item.url)"></image>					
							</view>
							<view>
								<view class="flex-item shop-text-align">
								<span class="shop-item-text">{{item.name}}</span>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>	
		</view>
		<hr>
		<!--商品展示 -->
		<view class="uni-flex uni-column">
			<view class="uni-flex-item flex-item-V">
				
			</view>
		</view>
		
	</view>
</template>

<script>
	/* 引入searchbar */
	import uniSearchBar from '@/components/uni-search-bar/uni-search-bar.vue'

	export default {
		data() {
			return {
				shopbannerFirst:[
					{
						name:"家具百货",
						img:"../../../static/家具百合.87003742.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"家电数码",
						img:"../../../static/家电数码.7095ae69.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"户外运动",
						img:"../../../static/户外运动.b6b84227.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"手表配饰",
						img:"../../../static/手表配饰.4b0244f7.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"服饰鞋靴",
						img:"../../../static/服饰鞋靴.77be142b.png",
						url:"../../shop/productdetailspage/productdetailspage"
					}
				],
				shopbannerSecond:[
					{
						name:"汽车用品",
						img:"../../../static/汽车用品.22076315.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"生活洗护",
						img:"../../../static/生活洗护.3b90dee6.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"皮具宝箱",
						img:"../../../static/皮具宝箱.f128a705.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"美妆个护",
						img:"../../../static/美妆个护.1608dca2.png",
						url:"../../shop/productdetailspage/productdetailspage"
					},
					{
						name:"酒水",
						img:"../../../static/酒水.b2b44949.png",
						url:"../../shop/productdetailspage/productdetailspage"
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
			    }
		},
		components: {
			uniSearchBar
		}
	}
</script>

<style>
	.item-size{
		width: 30%;
	}
	.img-div{
		padding-left: 15px;
	}
	.shop-item-size{
		width: 10%;
		height: 10%;
	}
	.shop-text-align{
		text-align: center;
		font-size: 20rpx;
		width: default;
	}
	.item-img{
		width: 80rpx;
		height: 80rpx;
		padding-left: 5rpx;
		padding-right: 5rpx;
	}
</style>
