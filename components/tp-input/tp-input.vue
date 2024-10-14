<template>
	<view>
		<view class="tp-input" :style="{width:(width+'rpx'),marginBottom:(marginBottom+'rpx')}">
			<input :placeholder="placeholder" @focus="isFocus=true" @blur="blur" @input="change"
				:class="[{inputActive:isFocus&&border},{inputError:validateFail&&border},'inp']"
				:style="{padding:padding}" :maxlength="maxlength" :auto-blur="true" :type="inputType"
				:password="inputType=='password'" v-model="value" />
			<view class="error-info" v-if="tipsMessage && validateFail">
				{{message}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "tp-input",
		props: {
			placeholder: {
				type: String,
				default: "请输入"
			},
			tipsMessage: { //是否显示错误提示
				type: Boolean,
				default: true
			},
			message: { //输入内容验证错误提示
				type: String,
				default: "输入不符合要求"
			},
			width: { //输入框宽度
				type: String,
				default: "654"
			},
			marginBottom: { //输入框下间距
				type: String,
				default: "48"
			},
			inputType: { //输入框类型
				type: String,
				default: "text"
			},
			maxlength: { //最大输入长度
				type: String,
				default: "140"
			},
			padding: { // 内边距
				type: String,
				default: "0 32rpx"
			},
			regexp: { // 验证输入内容正则
				type: RegExp,
				default: () => /\S+/
			},
			confirmPassword: { // 是否验证密码是否一致
				type: Array,
				default: () => []
			},
			border: { //是否显示边框
				type: Boolean,
				default: true
			}
		},
		data() {
			return {
				validateFail: false,
				isFocus: false,
				value: "",
			};
		},
		methods: {
			blur() {
				this.isFocus = false
				if (this.confirmPassword.length) {
					this.validateFail = this.confirmPassword[0] == this.confirmPassword[1] ? false : true
				} else {
					if (this.value) {
						this.validateFail = !this.regexp.test(this.value)
					} else {
						this.validateFail = false
					}
				}
				// this.validateFail?uni.$u.toast(this.message):""
			},
			change() {
				// 输入框内容改变时，向父组件传递输入内容和是否符合正则验证
				this.$emit("change", {
					value: this.value,
					validate: this.regexp.test(this.value)
				})
			},
			reset() {
				this.value = ''
			}
		}
	}
</script>

<style scoped>
	.tp-input {
		display: flex;
		flex-direction: column;
	}

	.inp {
		flex: 1;
		height: 80rpx;
		min-height: 80rpx;
		background: #F8F8F8;
		border-radius: 8rpx;
		border: 2rpx solid #F8F8F8;
		box-sizing: border-box;
		font-size: 29rpx;
		color: #333333;
		outline: none;
	}

	.inp::placeholder {
		color: #C0C4CC;
		/* Replace with your desired color */
	}

	.inp2 {
		padding: 0 32rpx !important;
	}

	.code-input {
		width: 410rpx;
		margin-right: 24rpx;
	}

	.inputActive {
		box-sizing: border-box;
		border: 2rpx solid #0075ff;
	}

	.inputError {
		box-sizing: border-box;
		border: 2rpx solid #FF5143;
	}

	.error-info {
		padding: 16rpx 0 0 32rpx;
		font-size: 24rpx;
		color: #FF5143;
		line-height: 34rpx;
	}
</style>