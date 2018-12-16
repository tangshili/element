<template>
	<el-card class="box-card">
		<div slot="header" class="clearfix">
			<span>请假条2</span>
			<el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>
		</div>
		<el-table :data="scores" style="width: 100%">
			<el-table-column type="index" width="50"></el-table-column>
			<el-table-column prop="name" label="姓名"></el-table-column>
			<el-table-column prop="chinese" label="手机号码"></el-table-column>
			<el-table-column prop="math" label="部门"></el-table-column>
			<el-table-column prop="english" label="请假时间"></el-table-column>
			<el-table-column label="操作">
				<template slot-scope="scope">
					<el-button size="mini" @click="dialogVisible=true;flag=true">同意</el-button>
					<el-button size="mini" type="danger" @click="dialogVisible=true;flag=false">驳回</el-button>
				</template>
			</el-table-column>
		</el-table>

		<el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="page" :page-sizes="[10]" :page-size="size" layout="total, sizes, prev, pager, next, jumper" :total="total">
		</el-pagination>
		
		
		<el-dialog
		  :title="flag?'同意请假':'驳回申请'"
		  :visible.sync="dialogVisible"
		  width="30%">
		 <el-input
  type="textarea"
  :rows="2"
  placeholder="意见"
  v-model="textarea">
</el-input>

		  <span slot="footer" class="dialog-footer">
		    <el-button @click="dialogVisible = false">取 消</el-button>
		    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
		  </span>
		</el-dialog>
		
	</el-card>
</template>

<script>
	export default {
		data() {
			return {
				flag:true,
				dialogVisible:false,
				size: 10,
				total: 100,
				page: 1,
				scores: []
			};
		},
		methods: {
			handleSizeChange(s) {
				this.scores =  this.getSocreList(s);
			},
			handleCurrentChange(p) {
				console.log(p);
				this.scores =  this.getSocreList(this.size);
			},
			getSocreList(n) {
				let arr = [];
				let names = ['张三','李四','王二','赵钱','孙李'];
				let partments = ['设计部','销售部','工程部','开发组','财务部'];
				for(let i = 0; i < n; i++) {
					let index = Math.floor(Math.random()*names.length);
					let s = {
						id: 1,
						name: names[index],
						chinese:'13'+Math.ceil(Math.random()*10000000000),
						math:partments[index],
						english: '20'+(Math.floor(Math.random()*2)+18)+'-'+Math.floor(Math.random()*12)+'-'+Math.floor(Math.random()*30)
					};
					arr.push(s);
				}
				return arr;
			}
		},created(){
			this.scores =  this.getSocreList(this.size);
		}
	}
</script>

<style>
	.el-pagination{
		margin-top: 20px;
		text-align: center;
	}

</style>