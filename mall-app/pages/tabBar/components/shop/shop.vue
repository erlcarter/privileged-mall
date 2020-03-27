<template>
	<view>
		
		<view class="uni-padding-wrap uni-common-mt">
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
						<!-- 家具百货 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">家具百货</span>
							</image>
						</view>
						<!-- 家电数码 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">家电数码</span>
							</image>
						</view>
						<!-- 户外运动 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">户外运动</span>
							</image>
						</view>
						<!-- 手表配饰 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">手表配饰</span>
							</image>
						</view>
						<!-- 服饰鞋靴 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">服饰鞋靴</span>
							</image>
						</view>
					</view>
					
					<view class="uni-flex uni-row">
						<!-- 汽车用品 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">汽车用品</span>
							</image>
						</view>
						<!-- 生活洗护 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">生活洗护</span>
							</image>
						</view>
						<!-- 皮具宝箱 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">皮具宝箱</span>
							</image>
						</view>
						<!-- 美妆个护 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">美妆个护</span>
							</image>
						</view>
						<!-- 酒水 -->
						<view class="flex-item item-size">
							<image class="shop-item-size" src="">
								<span class="shop-item-text">酒水</span>
							</image>
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
				
			}
		},
		methods: {
			
		},
		components: {
			uniSearchBar
		}
	}
</script>

<style>
	.item-size{
		width: 15%;
		height: 100rpx;
		margin: 3%;
	}
	.shop-item-size{
		width: 10%;
		height: 10%;
	}
	.shop-item-text{
		text-align: center;
		font-size: 20rpx;
	}
</style>
