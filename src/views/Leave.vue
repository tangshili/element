<template>
	<el-card class="leave">
		<div slot="header" class="clearfix">
			<span>请假条</span>
			<el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>
		</div>
		<div class="prepend">
			<el-input placeholder="请输入姓名……" v-model="input3">
				<template slot="prepend">姓名：</template>
			</el-input>
		</div>
		<div class="placeholder">
			<template>
				<el-select v-model="value" placeholder="部门">
					<el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value">
					</el-option>
				</el-select>
			</template>
		</div>
	</el-card>
</template>

<script>
	export default {
		data() {
			return {
				options: [{
					value: '选项1',
					label: '人事部门'
				}, {
					value: '选项2',
					label: '销售部门'
				}, {
					value: '选项3',
					label: '设计部门'
				}, {
					value: '选项4',
					label: '财务部门'
				}, {
					value: '选项5',
					label: '工程部门'
				}],
				value: ''
			}
		}
	}
</script>

<style>
	.leave .header {
		margin-bottom: 20px;
	}
</style>