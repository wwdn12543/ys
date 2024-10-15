<template>
	<view style="height: 100%">
		<!-- pages/about/about/about.wxml -->

		<cu-custom bgColor="bg-white" :isBack="true">
			<view slot="content">我的资料</view>
		</cu-custom>

		<scroll-view scroll-y class="scrollPage" style="min-height: 92vh;">
			<view class="cu-list menu card-menu sm-border margin-top margin-bottom-xl shadow radius">
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/about/about">
					<view class="content">
						<image src="/static/images/tabbar/basics_cur.png" class="png" mode="aspectFit"></image>
						<text>收货地址</text>
					</view>
				</view>
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/log/log">
					<view class="content">
						<text class="cuIcon-formfill text-blue"></text>
						<text>实名认证</text>
					</view>
				</view>
				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/appreciate/appreciate">
					<view class="content">
						<text class="cuIcon-wefill text-red"></text>
						<text>收款账号</text>
					</view>
				</view>
				<view class="cu-item arrow" @tap="toPage" data-url="https://github.com/XiaokangLei/ColorUI-GA">
					<view class="content">
						<text class="cuIcon-github text-black"></text>
						<text>支付密码</text>
					</view>
				</view>

				<view class="cu-item arrow" @tap="toPage" data-url="/pages/about/appreciate/withdraw">
					<view class="content">
						<text class="cuIcon-wefill text-red"></text>
						<text>登录密码</text>
					</view>
				</view>
			</view>
			
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {};
		},
		/**
		 * 生命周期函数--监听页面加载
		 */
		onLoad(options) {

		},

		methods: {

			toPage(e) {
				uni.navigateTo({
					url: e.currentTarget.dataset.url
				});
			}
		}
	};
</script>
<style>
	/* pages/about/about/about.wxss */
</style>