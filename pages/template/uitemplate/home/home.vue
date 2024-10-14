<template>
	<view style="height: 100%">
		<!-- pages/template/uitemplate/home/home.wxml -->
		<cu-custom bgColor="bg-white" :isBack="true">
			<view slot="content">资产申请</view>
		</cu-custom>

		<view style="min-height: 80vh">
			<view class="toast-fixed-center" v-if="show" style="z-index: 99">
				<view
					:class="'radius-lg padding animation-slide-top text-lg ' + (status == 'success' ? 'bg-green light' : 'bg-red light')">
					<text class="cuIcon-info"></text>
					{{ message }}
				</view>
			</view>

			<view class="zaiui-view-content">
				<!--用户数据-->
				<view class="padding-xs bg-white cu-card sqbd-box">
					<view class="text-black text-xl text-bold padding-sm">会员信息</view>
					<view class="inputs">
						<view class="title">姓名</view>
						<tp-input placeholder="请输入姓名" :border="false" @change="inputChange" maxlength="6"></tp-input>

						<view class="title">手机号</view>
						<tp-input @change="mobileChange" placeholder="请输入您的手机号" message="请输入正确的手机号" inputType="number"
							maxlength="11" :border="false" :regexp="/^[1][3,4,5,6,7,8,9][0-9]{9}$/"></tp-input>

						<view class="title">身份证号码</view>
						<tp-input placeholder="请输入您的身份证号码" :regexp="/(^\d{15}$)|(^\d{17}([0-9]|X)$)/"
							message="身份证号码不符合要求" maxlength="18" :border="false" @change="sfzChange"></tp-input>
					</view>
					
				</view>
				
				<view class="padding-xs bg-white cu-item ssjj-box">
					<view class="text-black text-xl text-bold padding-sm">受损金额</view>
					<view class="inputs">
						<tp-input placeholder="请输入你的受损金额" :border="false" v-model="money"></tp-input>
					</view>
				</view>
				
			
				<view class="bg-white pzsc-box">
				    <view class="text-black text-xl text-bold text-center padding-sm">凭证上传</view>
					<view class="cu-form-group">
					    <view class="grid col-1 grid-square flex-sub">
					        <view class="bg-img" @tap="ViewImage" :data-url="imgList[index]" v-for="(item, index) in imgList" :key="index">
					            <image :src="imgList[index]" mode="aspectFill"></image>
					
					            <view class="cu-tag bg-red" @tap.stop.prevent="DelImg" :data-index="index">
					                <text class="cuIcon-close"></text>
					            </view>
					        </view>
					        <view class="solids bg-gray" @tap="ChooseImage" v-if="imgList.length < 4">
					            <text class="cuIcon-cameraadd"></text>
					        </view>
					    </view>
					</view>
				</view>
				
				<view class="margin-top-xxl">
				    <button class="cu-btn block bg-blue margin-tb-sm lg round">提交</button>
				</view>

			</view>

		</view>
		<view class="cu-tabbar-height"></view>
		<view class="cu-tabbar-height"></view>
	</view>
</template>

<script>
	let loading = false;
	const animation = uni.createAnimation({
		duration: 400,
		timingFunction: 'ease-out',
		delay: 0,
		transformOrigin: '50% 50% 0'
	}); //动画
	let rewardedVideoAd = null;
	export default {
		data() {
			return {
				show: false,
				status: '',
				name: '',
				phone: '',
				idNumber: '',
				money: '',
				imgList: [],
				index: null,
				timeTop: 2000,
				modalName: ''
			};
		},
		/**
		 * 生命周期函数--监听页面加载
		 */
		onLoad() {
	
		},

		onShareAppMessage() {},
		methods: {

			// 轮播图跳转
			jumpTo(e) {
				return uni.navigateTo({
					url: e.currentTarget.dataset.page
				});
			},
			mobileChange(event) {
				this.phone = event.value;
			},
			inputChange(event) {
				this.name = event.value;
			},
			sfzChange(event) {
				this.idNumber = event.value;
			},
            ChooseImage() {
                uni.chooseImage({
                    count: 4,
                    //默认9
                    sizeType: ['original', 'compressed'],
                    //可以指定是原图还是压缩图，默认二者都有
                    sourceType: ['album'],
                    //从相册选择
                    success: (res) => {
                        if (this.imgList.length != 0) {
                            this.setData({
                                imgList: this.imgList.concat(res.tempFilePaths)
                            });
                        } else {
                            this.setData({
                                imgList: res.tempFilePaths
                            });
                        }
                    }
                });
            },
			ViewImage(e) {
			    uni.previewImage({
			        urls: this.imgList,
			        current: e.currentTarget.dataset.url
			    });
			},
			
			DelImg(e) {
			    uni.showModal({
			        title: '提示',
			        content: '确定要删除图片吗？',
			        cancelText: '取消',
			        confirmText: '确定',
			        success: (res) => {
			            if (res.confirm) {
			                this.imgList.splice(e.currentTarget.dataset.index, 1);
			                this.setData({
			                    imgList: this.imgList
			                });
			            }
			        }
			    });
			},

		}
	};
</script>
<style>
	/* pages/template/uitemplate/home/home.wxss */
	.sqbd-box {
		border-radius: 18.18rpx;
		margin-top: 72rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		.cu-list.grid.no-border {
			padding: 0;
		}

		.cu-list.grid.no-border>.cu-item {
			padding-bottom: 9.09rpx;
		}
	}
	
	.inputs {
		.title {
			margin-bottom: 24rpx;
			font-size: 30rpx;
			color: #0a0a0a;
			font-weight: bold;
		}
	}
	
	.ssjj-box {
		border-radius: 18.18rpx;
		margin-top: 35rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.pzsc-box {
		border-radius: 18.18rpx;
		margin-top: 35rpx;
	}
</style>