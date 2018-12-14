<template>
	<el-card class="leave">
		<div slot="header" class="clearfix" style="text-align: center; font-size:18px; font-weight: bold;">
			<span>请假条</span>
			<!--<el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>-->
		</div>

		<el-form ref="form" :model="form" label-width="100px">
			<el-row :gutter="20">

				<el-col :span="12">
					<el-form-item label="姓名：">
						<el-input v-model="form.name"></el-input>
					</el-form-item>
				</el-col>
				<el-col :span="12">
					<el-form-item label="手机号码：">
						<el-input v-model="form.name"></el-input>
					</el-form-item>
				</el-col>

			</el-row>
			<el-row :gutter="20">
				<el-col :span="12">
					<el-form-item label="紧急联系人：">
						<el-input v-model="form.name"></el-input>
					</el-form-item>
				</el-col>
				<el-col :span="12">
					<el-form-item label="手机号码：">
						<el-input v-model="form.name"></el-input>
					</el-form-item>
				</el-col>
			</el-row>

			<el-row :gutter="20">
				<el-col :span="12">
					<el-form-item label="部门">
						<el-select v-model="form.region" placeholder="请选择活动区域">
							<el-option label="人事部门" value="1"></el-option>
							<el-option label="销售部门" value="2"></el-option>
							<el-option label="设计部门" value="3"></el-option>
							<el-option label="财务部门" value="4"></el-option>
							<el-option label="工程部门" value="5"></el-option>
						</el-select>
					</el-form-item>
				</el-col>
				<el-col :span="12">
					<el-form-item label="请假时间">
						<el-col :span="11">

							<el-date-picker v-model="form.date1" type="datetimerange" start-placeholder="开始日期" end-placeholder="结束日期" :default-time="['12:00:00']">
							</el-date-picker>
						</el-col>
					</el-form-item>
				</el-col>
			</el-row>

			<el-form-item label="原因">
				<el-radio-group v-model="form.resource">
					<el-radio label="事假"></el-radio>
					<el-radio label="病假"></el-radio>
					<el-radio label="产假"></el-radio>
					<el-radio label="婚假"></el-radio>
					<el-radio label="其它"></el-radio>
				</el-radio-group>
			</el-form-item>
			<el-form-item label="备注：">
				<el-input type="textarea" v-model="form.desc"></el-input>
			</el-form-item>
			<el-form-item style="text-align: center;">
				
				
				<el-button type="primary" @click="open">提交</el-button>
				<el-button>重置</el-button>
			</el-form-item>
		</el-form>

	</el-card>
</template>

<script>
	export default {
		data() {
			return {
				form: {
					name: '',
					region: '',
					date1: '',
					date2: '',
					delivery: false,
					type: [],
					resource: '',
					desc: ''
				}
			}
		},
		methods: {
			onSubmit() {
				console.log('submit!');
			},
			open() {
				this.$notify({
					title: '成功',
					message: '提交成功！',
					type: 'success'
				});
			}
		}
	}
</script>

<style>

</style>