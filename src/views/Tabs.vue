<template>
	<el-card class="box-card">
		<div slot="header" class="clearfix">
			<span>tab切换</span>
			<el-button style="float: right; padding: 3px 0" type="text">操作按钮</el-button>
		</div>
		<el-tabs v-model="editableTabsValue2" type="card" closable @tab-remove="removeTab">
			<el-tab-pane v-for="(item, index) in editableTabs2" :key="item.name" :label="item.title" :name="item.name">
				{{item.content}}
			</el-tab-pane>
		</el-tabs>

	</el-card>
</template>

<script>
	export default {
		data() {
			return {
				editableTabsValue2: '2',
				editableTabs2: [{
					title: '用户管理',
					name: '1',
					content: '用户管理'
				}, {
					title: '配置管理',
					name: '2',
					content: '用户管理'
				}, {
					title: '角色管理',
					name: '3',
					content: '角色管理'
				}, {
					title: '定时任务补偿',
					name: '3',
					content: '定时任务补偿 '
				}],
				tabIndex: 2
			}
		},
		methods: {
			addTab(targetName) {
				let newTabName = ++this.tabIndex + '';
				this.editableTabs2.push({
					title: 'New Tab',
					name: newTabName,
					content: 'New Tab content'
				});
				this.editableTabsValue2 = newTabName;
			},
			removeTab(targetName) {
				let tabs = this.editableTabs2;
				let activeName = this.editableTabsValue2;
				if(activeName === targetName) {
					tabs.forEach((tab, index) => {
						if(tab.name === targetName) {
							let nextTab = tabs[index + 1] || tabs[index - 1];
							if(nextTab) {
								activeName = nextTab.name;
							}
						}
					});
				}

				this.editableTabsValue2 = activeName;
				this.editableTabs2 = tabs.filter(tab => tab.name !== targetName);
			}
		}
	}
</script>

<style>

</style>