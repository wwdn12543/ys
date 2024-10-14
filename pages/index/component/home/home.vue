<template>
	<view style="height: 100%">
		<!-- pages/index/component/home/home.wxml -->

		<cu-custom :noFixed="true" :isLucency="true">
			<view slot="content"><text class="text-white text-xl">诺亚方舟</text></view>
		</cu-custom>

		<!-- 全屏背景图 -->
		<image src="/static/images/6.png" mode="widthFix" class="bg-img-new"></image>

		<!-- 页面 -->
		<scroll-view scroll-y class="scrollPage">
			<view class="container">
				<view class="nav-list">
					<navigator open-type="navigate" hover-class="none" url="/pages/template/uitemplate/home/home"
						class="nav-li-new bg-gradual-cyan-light light">
						<view class="text-xl text-bold">完整UI模板</view>
						<view class="flex padding-top-xxl">
							<view class="flex-sub">基于ColorUI GA组件库实现商城、新闻、博客、企业网站等完整UI模板，持续开发更新中...</view>
						</view>
						<text class="cuIcon-hotfill"></text>
					</navigator>
				</view>
			</view>
			<view class="cu-tabbar-height"></view>
		</scroll-view>
	</view>
</template>

<script>
	const app = getApp();
	export default {
		data() {
			return {
				StatusBar: app.globalData.StatusBar,
				CustomBar: app.globalData.CustomBar,
				cardCur: 0,
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
			cardSwiper(e) {
				this.setData({
					cardCur: e.detail.current
				});
			},
			// 轮播图跳转
			jumpTo(e) {
				return uni.navigateTo({
					url: e.currentTarget.dataset.page
				});
			}
		},
		created: function() {}
	};
</script>
<style>
	/* pages/index/component/home/home.wxss */
	.image-bg {
		position: absolute;
		height: 100%;
		opacity: 0.5;
	}

	.nav-li-new {
		padding: 24rpx;
		border-radius: 20rpx;
		width: 98%;
		margin: 0 1% 32rpx;
		background-size: cover;
		background-position: center;
		position: relative;
		z-index: 1;
	}

	.nav-li-new::after {
		content: '';
		position: absolute;
		z-index: -1;
		background-color: inherit;
		width: 100%;
		height: 100%;
		left: 0;
		bottom: -10%;
		border-radius: 10rpx;
		opacity: 0.2;
		transform: scale(0.9, 0.9);
	}

	.nav-li-new.cur {
		color: #fff;
		background: rgb(94, 185, 94);
		box-shadow: 4rpx 4rpx 6rpx rgba(94, 185, 94, 0.4);
	}

	.nav-li-new text {
		position: absolute;
		right: 24rpx;
		top: 16rpx;
		font-size: 52rpx;
		width: 60rpx;
		height: 60rpx;
		text-align: center;
		line-height: 60rpx;
	}
</style>