<template>
	<view class="list_box">
		<view class="left">
			<scroll-view scroll-y="true" :style="{ 'height':scrollHeight }">
				<view class="item" 
					v-for="(item,index) in leftArray"
					:key="index" 
					:class="{ 'active':index==leftIndex }" 
					:data-index="index"
					@tap="leftTap"
				>{{item}}</view>
            </scroll-view>
		</view>
		<view class="main">
			<swiper class="swiper" :style="{ 'height':scrollHeight }" 
				:current="leftIndex" @change="swiperChange"
				 vertical="true" duration="300">
				<swiper-item v-for="(item,index) in mainArray" :key="index">
					<scroll-view  scroll-y="true" :style="{ 'height':scrollHeight }">
						<view class="item">
							<view class="title">
								<view>{{item.title}}</view>
							</view>
							<view class="goods" v-for="(item2,index2) in item.list" :key="index2">
								<image src="/static/logo.png" mode=""></image>
								<view>
									<view>第{{index2+1}}个商品标题</view>
									<view class="describe">第{{index2+1}}个商品的描述内容</view>
									<view class="money">第{{index2+1}}个商品的价格</view>
								</view>
							</view>
						</view>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				scrollHeight:'500px',
				leftArray:[],
				mainArray:[],
				leftIndex:0
			}
		},
		onLoad(){
			/* 设置当前滚动容器的高，若非窗口的高度，请自行修改 */
			uni.getSystemInfo({
				success:(res)=>{
					this.scrollHeight=`${res.windowHeight}px`;
				}
			});
		},
		mounted(){
			this.getListData();
		},
		methods: {
			/* 获取列表数据 */
			getListData(){
				// Promise 为 ES6 新增的API ，有疑问的请自行学习该方法的使用。
				new Promise((resolve,reject)=>{
					/* 因无真实数据，当前方法模拟数据。正式项目中将此处替换为 数据请求即可 */
					uni.showLoading();
					setTimeout(()=>{
						/* 因无真实数据，当前方法模拟数据 */
						let [left,main]=[[],[]];
						
						for(let i=0;i<10;i++){
							left.push(`${i+1}类商品`);
							
							let list=[];
							let max = Math.floor(Math.random()*15) || 8;
							for(let j=0;j<max;j++){
								list.push(j);
							}
							main.push({
								title:`第${i+1}类商品标题`,
								list
							})
						}
						
						// 将请求接口返回的数据传递给 Promise 对象的 then 函数。
						resolve({left,main});
					},1000);
				}).then((res)=>{
					console.log('-----------请求接口返回数据示例-------------');
					console.log(res);
					
					uni.hideLoading();
					this.leftArray=res.left;
					this.mainArray=res.main;
				});
			},
			/* 左侧导航点击 */
			leftTap(e){
				let index=e.currentTarget.dataset.index;
				this.leftIndex=Number(index);
			},
			/* 轮播图切换 */
			swiperChange(e){
				let index=e.detail.current;
				this.leftIndex=Number(index);
			}
		}
	}
</script>

<style lang="scss">
.list_box{
	display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    justify-content: flex-start;
    align-items: flex-start;
    align-content: flex-start;
	font-size: 28rpx;
	
	.left{
		width: 200rpx;
		background-color: #f6f6f6;
		line-height: 80rpx;
		box-sizing: border-box;
		font-size: 32rpx;
		
		.item{
			padding-left: 20rpx;
			position: relative;
			&:not(:first-child) {
				margin-top: 1px;
			
				&::after {
					content: '';
					display: block;
					height: 0;
					border-top: #d6d6d6 solid 1px;
					width: 620upx;
					position: absolute;
					top: -1px;
					right: 0;
					transform:scaleY(0.5);	/* 1px像素 */
				}
			}
			
			&.active,&:active{
				color: #42b983;
				background-color: #fff;
			}
		}
	}
	.main{
		background-color: #fff;
		padding-left: 20rpx;
		width: 0;
		flex-grow: 1;
		box-sizing: border-box;
		
		.swiper{
			height: 500px;
		}

		.title{
			line-height: 64rpx;
			font-size: 24rpx;
			font-weight: bold;
			color: #666;
			background-color: #fff;
			position: sticky;
			top: 0;
			z-index: 999;
		}
		
		.item{
			padding-bottom: 10rpx;
		}
		
		.goods{
			display: flex;
			flex-direction: row;
			flex-wrap: nowrap;
			justify-content: flex-start;
			align-items: center;
			align-content: center;
			margin-bottom: 10rpx;
			
			&>image{
				width: 120rpx;
				height: 120rpx;
				margin-right: 16rpx;
				margin-left: 2px;
			}
			
			.describe{
				font-size: 24rpx;
				color: #999;
			}
			
			.money{
				font-size: 24rpx;
				color: #efba21;
			}
		}
	}
}
</style>
