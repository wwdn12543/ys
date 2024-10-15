<template>
	<view style="height: 100%">
		<!-- pages/index/basics/home/home.wxml -->

		<cu-custom :noFixed="true" :isLucency="true">
			<view slot="content"><text class="text-white text-xl">首页</text></view>
		</cu-custom>

		<!-- 全屏背景图 -->
		<image src="/static/images/1.png" mode="widthFix" class="bg-img-new"></image>

		<!-- 页面 -->
		<scroll-view scroll-y class="scrollPage">
			<!-- 滚动图片 -->
			<swiper :class="'margin screen-swiper ' + (DotStyle ? 'square-dot' : 'round-dot')" :indicator-dots="false"
				:circular="true" :autoplay="true" interval="5000" duration="500"
				:style="'margin-top: ' + (StatusBar + CustomBar + 30) + 'rpx;'">
				<swiper-item class="radius" v-for="(item, index) in swiperList" :key="index">
					<image :src="item.url" mode="aspectFill" v-if="item.type == 'image'"></image>

					<video :src="item.url" autoplay loop muted :show-play-btn="false" :controls="false"
						objectFit="cover" v-if="item.type == 'video'"></video>
				</swiper-item>
			</swiper>

			<view class="zaiui-view-content">
				<view class="padding-xs bg-white margin-top zaiui-user-info-order-box">

					<view class="cu-list grid col-4 no-border">
						<view class="cu-item flex-sub margin-sm radius">
							<view>
								<image src="/static/images/2.png" class="cu-avatar md" :draggable="false"></image>
							</view>
							<text class="text-sm">App下载</text>
						</view>
						<view class="cu-item flex-sub margin-sm radius">
							<view>
								<image src="/static/images/3.png" class="cu-avatar md" :draggable="false"></image>
							</view>
							<text class="text-sm">社区资讯</text>
						</view>
						<view class="cu-item flex-sub margin-sm radius" @tap="order_list_tap">
							<view>
								<image src="/static/images/4.png" class="cu-avatar md" :draggable="false"></image>
							</view>
							<text class="text-sm">邀请好友</text>
						</view>
						<view class="cu-item flex-sub margin-sm radius">
							<view>
								<image src="/static/images/5.png" class="cu-avatar md" :draggable="false"></image>
							</view>
							<text class="text-sm">在线充值</text>
						</view>
					</view>
				</view>


				<view class="tips-boxs margin-tb radius-lg bg-white">
					<view class="text-black text-lg text-bold margin title">人民币汇率中间价</view>
					<view class="tips-box_i padding-lr padding-top-xs">
						<swiper class="tips-swiper" :vertical="true" :autoplay="true" :circular="true" interval="3000"
							:style="'height: ' + (list.length > 6 ? '460' : list.length * 60) + 'rpx;'"
							:display-multiple-items="list.length > 6 ? 7 : list.length">
							<block v-for="(item, idx) in list" :key="idx">
								<swiper-item>
									<view class="flex" style="align-items: baseline">
										<text :decode="true" class="cny-rate-item">{{ item.money_1 }}
											&nbsp;&nbsp;&nbsp;</text>
										<text :decode="true"
											class="cny-rate-item">&nbsp;&nbsp;{{ item.money_name1 }}</text>
										<text :decode="true" class="cny-rate-item">{{ item.money_2 }}
											&nbsp;&nbsp;&nbsp;</text>
										<text :decode="true"
											class="cny-rate-item">&nbsp;&nbsp;{{ item.money_name2 }}</text>
									</view>
								</swiper-item>
							</block>
						</swiper>
					</view>
				</view>

				<view class="cu-card article bg-white radius-lg margin-top">
					<view class="text-black text-lg text-bold margin title">新闻资讯</view>
					<view class="cu-item shadow">
						<view class="content">
							<image
								src="https://image.meiye.art/FlqKg5bugFQD5Qzm_QhGM7ET4Mtx?imageMogr2/thumbnail/450x/interlace/1"
								mode="aspectFill"></image>
							<view class="desc solid-bottom">
								<view class="text-content">创意是基于本质而来的解决方案。本质是什么，是不会因为其他外在条件而改变的东西。</view>
								<view>
									<view class="light sm margin-bottom-lg">2024-4-24</view>
								</view>
							</view>
						</view>
					</view>
					<view class="cu-item shadow">
						<view class="content">
							<image
								src="https://image.meiye.art/FlqKg5bugFQD5Qzm_QhGM7ET4Mtx?imageMogr2/thumbnail/450x/interlace/1"
								mode="aspectFill"></image>
							<view class="desc solid-bottom">
								<view class="text-content">创意是基于本质而来的解决方案。本质是什么，是不会因为其他外在条件而改变的东西。</view>
								<view>
									<view class="light sm margin-bottom-lg">2024-4-24</view>
								</view>
							</view>
						</view>
					</view>
					<view class="cu-item shadow">
						<view class="content">
							<image
								src="https://image.meiye.art/FlqKg5bugFQD5Qzm_QhGM7ET4Mtx?imageMogr2/thumbnail/450x/interlace/1"
								mode="aspectFill"></image>
							<view class="desc solid-bottom">
								<view class="text-content">创意是基于本质而来的解决方案。本质是什么，是不会因为其他外在条件而改变的东西。</view>
								<view>
									<view class="light sm margin-bottom-lg">2024-4-24</view>
								</view>
							</view>
						</view>
					</view>
				</view>

			</view>


			<view class="cu-tabbar-height"></view>
		</scroll-view>
		<template>
			<view v-if="isVisible" class="u-transition u-fade-enter-to u-fade-enter-active"
				style="transition-duration: 300ms; transition-timing-function: ease-out; position: fixed; inset: 0px; z-index: 999; background-color: rgba(0, 0, 0, 0.4);">
				<view class="warp2">
					<view class="rect2">
						<view class="close" @click="close">
							<view class="u-icon u-icon--right">
								<text class="u-icon__icon uicon-close-circle cuIcon-roundclose"
									style="font-size: 28px; line-height: 28px; font-weight: normal; top: 0px; color: white;">
									<span></span>
								</text>
							</view>
						</view>
						<view class="notice-content">
							<scroll-view style="height: 100%;">
								<view class="uni-scroll-view">
									<view class="uni-scroll-view" style="overflow: hidden auto;">
										<view class="uni-scroll-view-content">
											<view id="_root" class="_root">
												<view class="_undefined undefined">
													<text>
														<span>测试测试</span>
													</text>
												</view>
											</view>
										</view>
									</view>
								</view>
							</scroll-view>
						</view>
					</view>
				</view>
			</view>
		</template>
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
				isVisible: true,
				swiperList: [{
						id: 0,
						type: 'image',
						title: '布局UI设计',
						des: 'Flex、Grid及基础样式',
						url: 'https://image.meiye.art/FlqKg5bugFQD5Qzm_QhGM7ET4Mtx?imageMogr2/thumbnail/450x/interlace/1',
						page: '/pages/index/basics/layout/layout'
					},
					{
						id: 1,
						type: 'image',
						title: '背景UI设计',
						des: '纯色、渐变色图片背景等样式',
						url: 'https://image.meiye.art/Fha6tqRTIwHtlLW3xuZBJj8ZXSX3?imageMogr2/thumbnail/450x/interlace/1',
						page: '/pages/index/basics/background/background'
					},
					{
						id: 2,
						type: 'image',
						title: '文本UI设计',
						des: '文本大小、颜色及标题等样式',
						url: 'https://image.meiye.art/FhHGe9NyO0uddb6D4203jevC_gzc?imageMogr2/thumbnail/450x/interlace/1',
						page: '/pages/index/basics/text/text'
					}
				],
				list: [{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					},
					{
						money_1: '100',
						money_name1: '人民币',
						money_2: '573.56',
						money_name2: '俄罗斯卢布'
					}
				],
				DotStyle: false
			};
		},
		options: {
			addGlobalClass: true
		},
		/**
		 * 组件的方法列表
		 */
		methods: {
			cardSwiper(e) {
				this.setData({
					cardCur: e.detail.current
				});
			},
			jumpTo(e) {
				return uni.navigateTo({
					url: e.currentTarget.dataset.page
				});
			},
			close() {
				this.isVisible = false;
			}
		},
		
	};
</script>
<style>
	/* pages/index/basics/home/home.wxss */
	.image-bg {
		position: absolute;
		height: 100%;
		opacity: 0.5;
	}

	.zaiui-user-info-order-box {
		border-radius: 18.18rpx;

		.cu-list.grid.no-border {
			padding: 0;
		}

	}

	.title::before {
		width: 12px;
		height: 12px;
		content: "";
		position: absolute;
		left: 48rpx;
		background: linear-gradient(150.95deg, #0182ef, rgba(2, 131, 240, 0));
		border-radius: 50%;
		z-index: 1;
	}

	.flex .cny-rate-item {
		width: 25%;
		height: 35rpx;
		text-align: center;
		color: rgba(0, 0, 0, .8)
	}

	.warp2 {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100%;

		.rect2 {
			width: 325px;
			height: 659px;
			display: flex;
			align-items: center;
			justify-content: center;
			position: relative;
			background-image: url(/static/images/notice2.11501d25.jpg);
			background-size: 100% 100%;
			border-radius: 10px;

			.notice-content {
				position: absolute;
				top: 131px;
				left: 0;
				width: 100%;
				height: calc(100% - 131px);
				box-sizing: border-box;
				padding: 25px;
				font-size: 15px;

				.scroll-view-box {
					width: 100%;
					height: 100%;
					background-color: #fff;
					border-radius: 10px;
					box-sizing: border-box;
					padding: 5px;

					uni-scroll-view {
						width: 100%;
						height: 100%;
						padding: 5px;
						border-radius: 12px;
						box-sizing: border-box
					}
				}
			}

			.close {
				position: absolute;
				width: 25px;
				height: 25px;
				right: 12px;
				top: 8px;
				z-index: 9999
			}
		}
	}
</style>