<template>
	<view style="height: 100%">
		<!-- pages/about/home/home.wxml -->
		<cu-custom bgColor="bg-white" :noFixed="true" :isLucency="true">
			<view slot="content">我的</view>
		</cu-custom>
		<!-- 背景图 -->
		<image src="/static/images/29.png" mode="widthFix" class="bg-img-new"></image>

		<scroll-view scroll-y class="scrollPage">
			<view class="cu-list menu-avatar UCenter-bg">
				<view class="cu-item">
					<view class="cu-avatar round lg"
						style="background-image:url(https://image.meiye.art/FhHGe9NyO0uddb6D4203jevC_gzc?imageMogr2/thumbnail/450x/interlace/1);width: 4rem;height: 4rem;border: 2px solid #f91a41;">
					</view>
					<view class="content text-xl margin-left-lg">
						<view class="text-white">
							<text class="margin-right">仔仔</text>
						</view>
						<view class="text-white-bg text-sm">
							<text>邀请码 123123123</text>
						</view>
					</view>
					<view class="lg">
						<img class="" src="/static/images/71.png" style="width: 4rem;">
					</view>
				</view>
			</view>

			<view class="padding-top user-view radius-xl-top">
				<view class="nav-list margin-top">
					<navigator open-type="navigate" hover-class="none"
						:url="'/pages/about/basics/' + item.link + '/' + item.link" :class="'nav-li bg-' + item.color"
						v-for="(item, index) in elements" :key="index">
						<image src="/static/images/0004.svg" mode="widthFix" class="image-bg"
							style="z-index: -2; margin: -8rpx 0rpx 0rpx -32rpx"></image>

						<view class="nav-title">{{ item.title }}</view>

						<view class="flex">
							<view class="flex-sub nav-name">{{ item.name }}</view>
						</view>

					</navigator>
				</view>
			</view>

			<view class="cu-list menu card-menu sm-border margin-top margin-bottom-xl shadow radius-lg">
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/about/about">
					<view class="content">
						<image src="/static/images/tabbar/basics_cur.png" class="png" mode="aspectFit"></image>
						<text>我的资料</text>
					</view>
				</view>
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/log/log">
					<view class="content">
						<text class="cuIcon-formfill text-blue"></text>
						<text>我的资产</text>
					</view>
				</view>
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/appreciate/appreciate">
					<view class="content">
						<text class="cuIcon-wefill text-red"></text>
						<text>账号充值</text>
					</view>
				</view>
				<view class="cu-item arrow" @tap="CopyText" data-link="https://github.com/XiaokangLei/ColorUI-GA">
					<view class="content">
						<text class="cuIcon-github text-black"></text>
						<text>我的团队</text>
					</view>
					<view class="cuIcon-copy text-blue"></view>
				</view>
				<view class="cu-item arrow" @tap="CopyText" data-link="https://one.x-artspace.cn/ColorUI-GA-Docs">
					<view class="content">
						<text class="cuIcon-link text-green"></text>
						<text>在线客服</text>
					</view>
					<view class="cuIcon-copy text-blue"></view>
				</view>
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/appreciate/withdraw">
					<view class="content">
						<text class="cuIcon-wefill text-red"></text>
						<text>提现通道</text>
					</view>
				</view>
			</view>

			<!-- <view class="cu-list menu card-menu sm-border margin-top-sm shadow-lg">
				<button class="cu-btn block line-blue lg">
				   
				    退出
				</button>
			</view> -->
			<view class="padding-xl margin-top-sm radius-lg">
			    <button class="cu-btn block line-blue lg">
			        <text class="cuIcon-exit"></text>
			        退出登录
			    </button>
			</view>
			<view class="margin-top">
			</view>

			<view class="cu-tabbar-height"></view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				elements: [{
						title: '签到送积分',
						name: '累计积分换豪礼',
						color: 'blue light',
						link: 'sign'
					},
					{
						title: '积分兑换',
						name: '多重好礼等你兑换',
						color: 'cyan light',
						link: 'exchange'
					},
					{
						title: '福利工资',
						name: '衔级待遇月月领',
						color: 'purple light',
						link: 'salary'
					},
					{
						title: '等级特权 ',
						name: '升级会员专属福利',
						color: 'mauve light',
						link: 'grade'
					}
				]
			};
		},
		options: {
			addGlobalClass: true
		},
		/**
		 * 组件的属性列表
		 */
		props: {},
		/**
		 * 组件的方法列表
		 */
		methods: {

			coutNum(e) {
				if (e > 1000 && e < 10000) {
					e = (e / 1000).toFixed(1) + 'k';
				}
				if (e > 10000) {
					e = (e / 10000).toFixed(1) + 'W';
				}
				return e;
			},

			CopyText(e) {
				uni.setClipboardData({
					data: e.currentTarget.dataset.link,
					success: (res) => {
						uni.showToast({
							title: '链接已复制',
							duration: 1000
						});
					}
				});
			},

			toPage(e) {
				uni.navigateTo({
					url: e.currentTarget.dataset.url
				});
			}
		},
		mounted() {

		},
		created: function() {}
	};
</script>
<style>
	/* pages/about/home/home.wxss */
	.UCenter-bg {
		/* background-image: url("https://image.weilanwl.com/color2.0/index.jpg"); */
		background-size: cover;
		height: 480rpx;
		display: flex;
		/* justify-content: center; */
		padding-top: 240rpx;
		overflow: hidden;
		position: relative;
		flex-direction: column;
		/* align-items: center; */
		color: #fff;
		font-weight: 300;
		text-shadow: 0 0 3px rgba(0, 0, 0, 0.3);
	}

	.UCenter-bg .text {
		opacity: 0.8;
	}

	.png {
		width: 200rpx;
		height: 200rpx;
	}

	.UCenter-bg .gif-wave {
		position: absolute;
		width: 100%;
		bottom: 0;
		left: 0;
		z-index: 99;
		mix-blend-mode: screen;
		height: 100rpx;
	}

	.user-view {
		margin-top: -76rpx;
		background-color: #f1f1f1;
	}

	.image-bg {
		position: absolute;
		height: 100%;
		opacity: 0.5;
	}
</style>