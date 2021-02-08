<template>
	<view class="msb_dialog" v-if="dialogShow" :style="fullHeight">
		<view class="dialog_1">
			<view class="dialog_title">标题</view>
			<view class="dialog_content">
				<view class="content" :class="{'active':dialogCurrent==item.id}" @click="addMenu(item.id)" v-for="(item, id) in dialogContent" :key="item.id">{{ item.name }}</view>
			</view>
			<view class="dialog_input">
				<input type="text" value="" :placeholder="placeholder"/>
			</view>
			<view class="dialog_btn">
				<button @click="btnCancel" class="btn btn1">取消</button>
				<button @click="btnSubmit" class="btn btn2">确定</button>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	name: 'msbDialog',
	props: {
		dialogShow: {
			type: Boolean,
			default: () => {}
		},
		dialogContent: {
			type: Array,
			default: () => {}
		},
		placeholder:{
			type: String,
			default:() => {
				
			}
		},
		dialogCurrent:{
			type:Number,
			default:() => {
				
			}
		}
	},
	data() {
		return {
			fullHeight: ''
		};
	},
	methods: {
		btnCancel() {
			this.$emit('changeCancelMenu', false);
		},
		btnSubmit() {
			this.$emit('changeconfirm', false);
		},
		addMenu(e){
			console.log(e)
			this.$emit('changeMenu',e)
		}
	},
	mounted() {
		console.log(this.dialogCurrent)
	},
	created() {
		let that = this;
		uni.getSystemInfo({
			success: function(res) {
				that.fullHeight = 'height:' + res.windowHeight + 'px';
			}
		});
	}
};
</script>

<style lang="less" scoped>
.msb_dialog {
	width: 100%;
	height: 100vh;
	position: fixed;
	left: 0;
	right: 0;
	bottom: 0;
	z-index: 9999;
	background: rgba(0, 0, 0, 0.8);
	.dialog_1 {
		margin: 30rpx;
		border-radius: 20rpx;
		background: #fff;
		position: relative;
		top: 50%; /*偏移*/
		transform: translateY(calc(-50% - 60rpx));
		.dialog_input{
			margin: 0 30rpx 30rpx;
			padding: 30rpx 20rpx;
			border: 1rpx solid #ccc;
		}
		.dialog_title {
			font-size: 32rpx;
			font-weight: 600;
			padding-top: 20rpx;
			text-align: center;
		}
		.dialog_content {
			padding: 30rpx;
			display: -webkit-flex;
			display: flex;
			-webkit-flex-wrap: wrap;
			flex-wrap: wrap;
			.content {
				width: 160rpx;
				line-height: 60rpx;
				margin: 20rpx;
				border-radius: 10rpx;
				text-align: center;
				overflow:hidden;
				white-space: nowrap;
				text-overflow: ellipsis;
			    -o-text-overflow:ellipsis;
				border: 1rpx solid #666;
			}
			.active{
				background: #3183ff;
				border: none;
				color: #fff;
			}
		}
		.dialog_btn {
			display: flex;
			flex-direction: row;
			align-items: center;
			.btn {
				flex: 1;
				border-radius: 0;
				color: #000;
				background: none;
			}
			.btn::after {
				border-radius: 0;
			}
			.btn1 {
				color: #666;
			}
			.btn2 {
				color: #3183ff;
			}
		}
	}
}
</style>
