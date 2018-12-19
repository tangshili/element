<template>
	<div class="home">
		<h1>{{msg}}</h1>
		<h1>{{count}}</h1>
		<h1>{{arr}}</h1>
		<h1>奇数：{{odd}}</h1>
		<h1>偶数：{{even}}</h1>		
		<button @click="add(5)">+</button><!--{{count}}--><button @click="reduce(5)">-</button><br />
		<button @click="addAction">dispatch</button>
	</div>
</template>

<script>
	import { mapState,mapGetters,mapMutations,mapActions } from "vuex";

	export default {
		name: 'home',
		computed: {
			//			count() {
			//				return this.$store.state.count;
			//			},

			...mapState(['count','msg','arr']),
			...mapGetters(['odd','even'])

		},
		methods:{
			...mapMutations(['add','reduce']),
			...mapActions(['addAction'])
		},
		components: {}
	}
</script>