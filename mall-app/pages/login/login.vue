<template>
	<view class="content">
		<image class="logo" src="../../static/img/logo.png"></image>
			<view class="input-group">
				<view class="input-row border">
					<text class="title">账号：</text>
					<m-input class="m-input" type="text" clearable focus v-model="account" placeholder="请输入账号"></m-input>
				</view>
				<view class="input-row">
					<text class="title">密码：</text>
					<m-input type="password" displayable v-model="password" placeholder="请输入密码"></m-input>
				</view>
			</view>
			<view class="btn-row">
				<button class="cu-btn bg-green block lg" @tap="bindLogin">登录</button>
			</view>
			<view class="action-row">
				<navigator url="../reg/reg">注册账号</navigator>
				<text>|</text>
				<navigator url="../pwd/pwd">忘记密码</navigator>
			</view>
		</view>
	</view>
	
	<!-- <button type="primary" @tap="btn">登录</button> -->
</template>

<script>
	import service from '../../service.js';
	import {
		mapState,
		mapMutations
	} from 'vuex'
	import mInput from '../../components/m-input.vue'
	
	export default {
		components:{
			mInput
		},
		data() {
			return {
				providerList: [],
				hasProvider: false,
				account: '',
				password: '',
				positionTop: 0,
				isDevtools: false,
			}
		},
		computed: mapState(['forcedLogin']),
		methods: {
			mapMutations(['login']),
			initPosition() {
				/**
				 * 使用 absolute 定位，并且设置 bottom 值进行定位。软键盘弹出时，底部会因为窗口变化而被顶上来。
				 * 反向使用 top 进行定位，可以避免此问题。
				 */
				this.positionTop = uni.getSystemInfoSync().windowHeight - 100;
			},
			bindLogin() {
				/**
				 * 客户端对账号信息进行一些必要的校验。
				 * 实际开发中，根据业务需要进行处理，这里仅做示例。
				 */
				if (this.account.length < 5) {
					uni.showToast({
						icon: 'none',
						title: '账号最短为 5 个字符'
					});
					return;
				}
				if (this.password.length < 6) {
					uni.showToast({
						icon: 'none',
						title: '密码最短为 6 个字符'
					});
					return;
				}
				/**
				 * 下面简单模拟下服务端的处理
				 * 检测用户账号密码是否在已注册的用户列表中
				 * 实际开发中，使用 uni.request 将账号信息发送至服务端，客户端在回调函数中获取结果信息。
				 */
				const data = {
					account: this.account,
					password: this.password
				};
				const validUser = service.getUsers().some(function(user) {
					return data.account === user.account && data.password === user.password;
				});
				if (validUser) {
					console.log(this.account)
					this.toMain(this.account);
				} else {
					uni.showToast({
					icon: 'none',
					title: '用户账号或密码不正确',
					});
				}
			},
			getUserInfo({
				detail
			}) {
				if (detail.userInfo) {
					this.toMain(detail.userInfo.nickName);
				} else {
					uni.showToast({
						icon: 'none',
						title: '登陆失败'
					});
				}
			},
			toMain(userName) {
				this.login(userName);
				/**
				 * 强制登录时使用reLaunch方式跳转过来
				 * 返回首页也使用reLaunch方式
				 */
				if (this.forcedLogin) {
					uni.reLaunch({
						url: '../main/main',
					});
				} else {
					uni.navigateBack();
				}

			}
			
	/* 		//登录
			btn() {
				//事件处理
				if (this.username.length <= 0) {
					uni.showToast({
						icon: 'none',
						title: '请输入用户名'
					});
					return;
				}
				if (this.pwd.length <= 0) {
					uni.showToast({
						icon: 'none',
						title: '请输入密码'
					});
					return;
				}
				//网络请求
			uni.request({
				url: 'http://127.0.0.1:8080/ZycfService/login/login', //仅为示例，并非真实接口地址。
				data: {
					username: this.username,
					pass: this.pwd
				},
				success: (res) => {
					let list = JSON.stringify(res.data);
					console.log("返回数据状态:" + list);
					if (list == "[]") {
						uni.showToast({
							icon: 'none',
							title: '用户名或密码错误'
						});
						return;
					}

					uni.showToast({
						icon: 'none',
						title: '登录成功'
					});
				},
				fail: () => {
					uni.showToast({
						icon: 'none',
						title: '网络异常,请稍后重试'
					});
				}
			});
		},
			//解析数据，存储本地
			let list = JSON.stringify(res.data);
			console.log("返回数据状态:" + list);
			if (list == "[]") {
				uni.showToast({
					icon: 'none',
					title: '用户名或密码错误'
				});
				return;
			}
			const data = res.data;
			self.lists = data;
			// console.log("返回数据状态:" + JSON.stringify(res));

			console.log("返回数据状态:" + self.lists[0]['rolename']);

			uni.setStorage({
				key: 'userinfo',
				data: {
					bh: self.lists[0]['bh'],
					rolename: self.lists[0]['rolename'],
					username: self.lists[0]['username']

				}
			})
			//跳转页面
			uni.navigateTo({
				url: '../home/home',
			});*/
		
		} ,
		onReady() {
			this.initPosition();
		}	
	}
</script>

<style>
	.action-row {
		display: flex;
		flex-direction: row;
		justify-content: center;
		color: #39B54A;
	}

	.action-row navigator {
		color: #39B54A;
		padding: 0 10px;
	}

	.logo {
		width: 250upx;
		height: 250upx;
		border-radius: 50%;
		margin: 50px auto 20px auto;
	}
</style>
