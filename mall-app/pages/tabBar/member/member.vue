<template>
	<view>
		<view class="uni-padding-wrap uni-common-mt">
			<!-- 个人信息展示 -->
			<uni-card class="card-size">
				<view class="uni-flex uni-column">
					<view class="flex-item sub-itemleft-size">
						<image class="user-img-size" src="../../../../static/logo.png"></image>
					</view>
					<view class="flex-item sub-itemleft-size">
						<view class="uni-flex uni-row">
							<view class="flex-item hr-size"><hr></view>
							<view class="flex-item uname-size">username</view>
							<view class="flex-item hr-size"><hr></view>
						</view>
						<view class="uni-flex uni-row">
							<!-- 普通会员 -->
						</view>
					</view>
				</view>
			</uni-card>
			<!-- 超级会员尊享特权 -->
			<uni-card class="card-size">
				<view class="uni-flex uni-column">
					
				</view>
			</uni-card>
			<!-- 邀请好友关注升级 -->
			<uni-card class="card-size">
				<view class="uni-flex uni-column">
					
				</view>
			</uni-card>
		</view>
	</view>
</template>

<script>
	/* 引入卡片式布局 */
	import uniCard from '@/components/uni-card/uni-card.vue'
	
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		components: {
			uniCard
		}
	}
</script>

<style>
	.card-size{
		width: 100%;
		height: 350rpx;
		margin: 50rpx 0;
	}
	.user-img-size{
		width: 125rpx;
		height: 125rpx;
		margin-left: 260rpx;
		margin-right: 260rpx;
	}
	.hr-size{
		background-color: #007AFF;
		width: 40%;
		height: 2px;
		margin-left: 5%;
		margin-right: 5%;
		margin-top: 5%;
		margin-bottom: 5%;
	}
	.uname-size{
		color: #007AFF;
		width: 20%;
		height: 10%;
		margin-top: 1%;
		margin-bottom: 1%;
		font-weight: bold;
		text-align: center;
	}
</style>
