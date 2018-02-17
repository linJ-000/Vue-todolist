<template>
	<div class="item" 
		v-bind:class="{completed: item.completed}" 
		@click='completed'>
			{{item.content}}
		
		<div class="del"  @click="del">X</div>
	</div>
</template>

<script type="text/javascript">
export default{
	props:{
		item:{
			type:Object,
			required: true
		}
	},
	methods:{
		completed:function(){
			this.$emit('completed', this.item.id);
		},
		del:function(){
			this.$emit('del', this.item.id);
		}
	}
}
</script>

<style type="text/css">
.item{
	width: 80%;
	max-width: 500px;
	min-height: 25px;
	font-size: 15px;
	line-height: 25px;
	text-align: left;
	margin: 10px auto;
	border-bottom: solid 1px #35495e;
	cursor: pointer;
}
.del{
	display: inline-block;
	width: 20px;
	height: 20px;
	margin: 2.55px 2.55px;
	float: right;
	font-size: 15px;
	cursor: pointer;
}
.completed{
	text-decoration: line-through;
	color: 	#87CEFA;
	border-bottom: solid 1px #87CEFA;
}
</style>