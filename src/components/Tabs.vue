<template>

	<el-tabs v-model="activePath" @tab-click="handleClick" @tab-remove="handleRemove">
		<el-tab-pane :name="tab.path" :key="index" v-for="(tab,index) in tabs" :closable="index!=0">
			<span slot="label">
			 	<i :class="tab.icon"></i>&nbsp;<span v-text="tab.title"></span>
			</span>
		</el-tab-pane>
	</el-tabs>

</template>

<script>
	import { mapState, mapMutations } from "Vuex";
	export default {
		data() {
			return {};
		},
		computed: {
			...mapState(['tabs']),
			activePath: {
				set(path) {
					console.log(path),
						this.switchTab(path);
				},
				get() {
					return this.$store.state.activePath;
				}
			}
		},
		methods: {
			...mapMutations(['switchTab']),
			handleClick(tab) {
				this.$router.push(this.activePath);
			},
			handleRemove(name) {
				this.tabs = this.tabs.filter(item => item.path != name);
				this.activeName = this.tabs[0].path;
				this.$router.pusth(this.activeName);
			}
		}
	}
</script>

<style>

</style>