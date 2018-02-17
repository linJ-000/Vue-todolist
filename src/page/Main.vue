<template>
	<div id="main">
		<ahead/>
		<todo/>
		<afoot/>
	</div>
</template>

<script>
import ahead from '../components/Header.vue'
import todo from '../components/Todo.vue'
import afoot from '../components/Footer.vue'
export default{
	name: 'Main',
	data () {
		return {
			title: 'todo list'
		}
	},
	components:{
		ahead,
		todo,
		afoot
	}
}
</script>

<style>
#main{
	color: #35495e;
}
</style>