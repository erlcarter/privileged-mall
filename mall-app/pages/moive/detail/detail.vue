<template>
	
	<view class="content">
		<!--  播放器 -->
		<view 
		class="video-player"
		:style="'background-image: url('+ movie.src +'); background-repeat: no-repeat;background-size: 100% 230px;'">
			<text class="player-icon text-white cuIcon-playfill" @tap="goSplayer"></text>
		</view>
		<!--  影片详情 -->
		<view class="video-content">
			<view class="video-title">
				<view class="video-name">
					 {{movie.title}}
				</view>
				<view class="video-sd">
					 简介
				</view>
				<text class="video-more text-gray" :class="showDesc?'cuIcon-fold':'cuIcon-unfold'" @tap="ifShowDesc"></text>
			</view>
			<view class="video-desc">
				<view class="actors">
					 主演:{{movie.actors}}
				</view>
				<view class="desc" v-show="showDesc">
					{{movie.desc}}
				</view>
			</view>
		</view>
		<!--  选项 -->
		<view class="video-opt">
			<view class="opt bg-gradual-blue">
				<text class="opt-icon text-white cuIcon-down"></text>
				<view class="opt-name">
					下载
				</view>
			</view>
			<view class="opt bg-gradual-blue">
				<text class="opt-icon text-white cuIcon-pick"></text>
				<view class="opt-name">
					 浏览器打开
				</view>
			</view>
			<view class="opt bg-gradual-blue">
				<text class="opt-icon text-white cuIcon-forwardfill"></text>
				<view class="opt-name">
					分享
				</view>
			</view>
		</view>
		<!--  资源列表 -->
		<view class="video-source-title">
			<view class="source-title">
				 选择资源
			</view>
			<view class="source-desc">
				无法观看尝试切换资源
			</view>
		</view>
		<view class="video-source">
			<view class="source bg-gradual-blue">
				 神力云
			</view>
			<view class="source bg-gradual-blue">
				  百度云
			</view>
		</view>
		<!--  选集 -->
		<view class="video-choise-title">
			<view class="choise-title">
				 选集
			</view>
			<view class="source-name">
				 当前资源: 神力云
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		components:{
			
		},
		data() {
			return {
				showDesc: false,
				movie:{
					'id': 0,
					'title': '大黄蜂',
					'src': 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2848803552,3617688781&fm=26&gp=0.jpg',
					'actors': '海莉·斯坦菲尔德，小豪尔赫·兰登伯格，约翰·塞纳，迪伦·奥布莱恩',
					'desc': '　汽车人在塞伯坦星内战中输给霸天虎之后，擎天柱将麾下成员派往宇宙各处，寻找可以重建军队的避风港。大黄蜂被派到地球，在1987年登陆加州时丧失了声音。大黄蜂将自己伪装成一辆大众甲壳虫，被正在经历丧父之痛的少女查莉·沃特森所救。她与大黄蜂成为了朋友，但很快发现他正在被追杀，同时，一个由特工杰克·伯恩斯领导的政府秘密组织“第七区”也盯上了他。在霸天虎成员背叛“第七区”并抓住大黄蜂之后，查理和她的邻居咪莫与特工伯恩斯组队营救大黄蜂，并在霸天虎征服地球之前打败了他们。',
					'url': 'http://api.47ks.com/webcloud/?v=https://www.iqiyi.com/v_19rrduqzgk.html'
				}
			}
		},
		methods: {
			ifShowDesc(){
				this.showDesc = !this.showDesc;
			},
			goSplayer(){
				uni.setStorage({
					key: 'video-name',
					data: 'http://api.47ks.com/webcloud/?v=https://www.iqiyi.com/v_19rrduqzgk.html',
					success() {
						console.log('success');
					}
				})
				uni.navigateTo({
					url: "../Splayer/Splayer"
				})
			},
		}
	}
</script>

<style>
	@import url('./index.css');
</style>
