<template>
    <view style="height: 100%">
        <!-- pages/template/home/home.wxml -->

        <cu-custom :noFixed="true" :isLucency="true">
            <view slot="content"><text class="text-white text-xl">云数币</text></view>
        </cu-custom>

        <!-- 背景图 -->
        <image src="/static/images/9.png" mode="widthFix" class="bg-img-new"></image>

        <!-- 页面 -->
        <scroll-view scroll-y class="scrollPage">
            
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
            swiperList: [
                {
                    id: 0,
                    type: 'image',
                    title: 'ColorUI GA',
                    des: '轻量、可靠的UI组件库',
                    url: 'https://image.meiye.art/FhHGe9NyO0uddb6D4203jevC_gzc?imageMogr2/thumbnail/450x/interlace/1',
                    page: '/pages/about/about/about'
                },
                {
                    id: 1,
                    type: 'image',
                    title: 'ColorUI GA',
                    des: '每周上新UI模板设计~',
                    url: 'https://image.meiye.art/Fha6tqRTIwHtlLW3xuZBJj8ZXSX3?imageMogr2/thumbnail/450x/interlace/1',
                    page: '/pages/template/login/home/home'
                },
                {
                    id: 2,
                    type: 'image',
                    title: 'ColorUI GA',
                    des: 'CSS样式、适合多种平台',
                    url: 'https://image.meiye.art/FlqKg5bugFQD5Qzm_QhGM7ET4Mtx?imageMogr2/thumbnail/450x/interlace/1',
                    page: '/pages/about/about/about'
                }
            ],
            elements: [
                {
                    title: '首页',
                    name: 'index',
                    color: 'purple light',
                    icon: 'homefill'
                },
                {
                    title: '个人中心',
                    name: 'user',
                    color: 'red light',
                    icon: 'profilefill'
                },
                {
                    title: '用户列表 ',
                    name: 'userlist',
                    color: 'mauve light',
                    icon: 'friendfill'
                },
                {
                    title: '评论页',
                    name: 'comment',
                    color: 'pink light',
                    icon: 'communityfill'
                },
                {
                    title: '消息列表',
                    name: 'message',
                    color: 'brown light',
                    icon: 'messagefill'
                },
                {
                    title: '音乐播放',
                    name: 'music',
                    color: 'green light',
                    icon: 'musicfill'
                },
                {
                    title: '书籍学习',
                    name: 'education',
                    color: 'orange light',
                    icon: 'formfill'
                },
                {
                    title: '登录注册',
                    name: 'login',
                    color: 'blue light',
                    icon: 'myfill'
                },
                {
                    title: '新闻资讯',
                    name: 'news',
                    color: 'pink light',
                    icon: 'news'
                },
                {
                    title: '榜单',
                    name: 'rank',
                    color: 'mauve light',
                    icon: 'rankfill'
                }
                // {
                //   title: '医疗健康',
                //   name: 'emoji',
                //   color: 'pink light',
                //   icon: 'creative'
                // },
            ],

            Headlines: [
                {
                    id: 1,
                    title: 'ColorUI GA 最新版v2.1.1上线啦~'
                },
                {
                    id: 2,
                    title: '新增新闻资讯模板+3'
                },
                {
                    id: 3,
                    title: '每周上新UI模板设计~'
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
        },

        falseFun() {
            console.log('占位：函数 false 未声明');
        }
    },
    created: function () {}
};
</script>
<style>
/* pages/template/home/home.wxss */

.cardTitle {
    padding: 90rpx 60rpx;
    font-size: 40rpx;
    font-weight: 300;
    transform: skew(-10deg, 0deg);
    position: relative;
    text-shadow: 0px 0px 6rpx rgba(0, 0, 0, 0.3);
}

.cardTitle::before {
    content: '';
    position: absolute;
    width: 60rpx;
    height: 6rpx;
    border-radius: 24rpx;
    display: block;
    top: 60rpx;
    left: 50rpx;
    transform: skew(10deg, 0deg);
}

.cardTitle::after {
    content: '';
    position: absolute;
    width: 140rpx;
    border-radius: 16rpx;
    height: 24rpx;
    background-color: rgb(223, 47, 47);
    display: block;
    bottom: 76rpx;
    left: 90rpx;
    transform: skew(10deg, 0deg);
    opacity: 0.1;
}

.image-bg {
    position: absolute;
    height: 100%;
    opacity: 0.5;
}

.swiperitem {
    height: 80rpx;
}

.cu-bar {
    display: flex;
    position: relative;
    align-items: center;
    min-height: 60rpx;
    justify-content: space-between;
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
