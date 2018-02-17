<template>
	<div id="tags">
		<p>{{undoNum}} items left</p>
		<span 
			v-for="state in states" 
			:key="state" 
			:class="[state === filter ? 'active' : '']" 
			@click="changeState(state)">
				{{state}}
		</span>
		<span @click="clear" class="clear">delete completed</span>
	</div>
</template>

<script type="text/javascript">
export default{
	props:{
		items:{
			type: Array,
			required: true
		},
		filter:{
			type:String,
			required:true
		}
	},
	data (){
		return {
			states:['all', 'undo', 'completed'],
		}
	},
	methods:{
		changeState(state){
			this.$emit('filterToggle', state)
		},
		clear(){
			this.$emit('clear')
		}
	},
	computed:{
		undoNum(){
			let num = 0
			for (var i = this.items.length - 1; i >= 0; i--) {
				if(!this.items[i].completed)
					num++
			}
			return num
		}
	}
}
</script>

<style type="text/css">
#tags{
	width: 80%;
	margin:0 auto;
	overflow: hidden;
	max-width: 500px;
	padding-bottom: 30px;
}
span{
	display: inline-block;
	padding: 2px;
	float: left;
	margin-right: 2px;
}
.clear{
	float: right;

}
.clear:hover{
	cursor: pointer;
	border:solid 1px #35495e;
	border-radius: 2px;
}
.active{
	border:solid 1px #35495e;
	border-radius: 2px;
}
</style>