<template>
	<view class="index">
		<view class="index_1">
			<view class="add_question">
				<!-- 打开dialog -->
				<button @click="openClick" hover-class="none" class="btn">内容提示框</button>
				<!-- msb内容遮罩层弹窗 :dialog-cancel=""-->
				<msb-dialog :dialog-show="configuration.dialogShow" @changeCancel="cancel" @changeconfirm="confirm"></msb-dialog>
				<!-- 打开dialog -->
				<button @click="menuClick" hover-class="none" class="btn001">添加菜单选项</button>
				<!-- msb菜单遮罩层弹窗 -->
				<menu-dialog :dialog-show="configurationMenu.dialogShow" :dialog-content="configurationMenu.content" @changeMenu="changeMenu" :dialog-current="configurationMenu.current" :placeholder="configurationMenu.placeholder" @changeCancelMenu="cancelMenu"></menu-dialog>
			</view>
		</view>
	</view>
</template>

<script>
import msbDialog from '../components/msb-dialog/msb-dialog.vue';
import menuDialog from '../components/menu-dialog/menu-dialog.vue';
export default {
	name: 'index',
	components: {
		msbDialog,
		menuDialog
	},
	data() {
		return {
			configuration: {
				dialogShow: false,
				title: '标题',
				content: '内容区域'
			},
			configurationMenu: {
				dialogShow: false,
				title: '标题',
				current:0,
				placeholder:'请输入你要添加的角色菜单',
				content: [
					{
						id: 0,
						name: '吕布'
					},
					{
						id: 1,
						name: '鲁班七号'
					},
					{
						id: 2,
						name: '干将莫邪'
					},
					{
						id: 3,
						name: '鲁班'
					},
					{
						id: 4,
						name: '孙尚香'
					},
					{
						id: 5,
						name: '扁鹊'
					},
					{
						id: 6,
						name: '打野猴子'
					},
					{
						id: 7,
						name: '上单诺克萨斯'
					}
				]
			}
		};
	},
	methods: {
		// 内容弹窗
		openClick() {
			this.configuration.dialogShow = !this.configuration.dialogShow;
		},
		// 取消
		cancel(e) {
			console.log(e);
			this.configuration.dialogShow = e;
		},
		// 确定
		confirm(e) {
			console.log(e);
			this.configuration.dialogShow = e;
		},
		// 菜单弹窗
		menuClick() {
			this.configurationMenu.dialogShow = !this.configurationMenu.dialogShow;
		},
		cancelMenu(e) {
			console.log(e);
			this.configurationMenu.dialogShow = e;
		},
		// 菜单选项
		changeMenu(e){
			this.configurationMenu.current = e
			},
	}
};
</script>

<style lang="less" scoped>
.index {
	position: relative;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	.add_question {
		padding: 0 30rpx;
		.btn {
			background: #199d33;
			padding: 30rpx;
			line-height: 60rpx;
			margin: 30rpx auto;
			color: #fff;
		}
		.btn001 {
			background: #3183ff;
			padding: 30rpx;
			line-height: 60rpx;
			margin: 30rpx auto;
			color: #fff;
		}
	}
}
</style>
