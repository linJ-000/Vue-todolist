<template>
	<div id="todo">
		<input 
			type="text"
			@keyup.enter="addItem"
			autofocus="autofocus"
			placeholder="what to do next" 
		/>
		<tags :items="items" :filter="filter" @filterToggle="filterToggle" @clear="clear"/>
		<item v-for="item in itemsFilter" :item="item" :key="item.id" @completed="completed" @del="del" />
	</div>
</template>

<script type="text/javascript">
import item from '../components/Item.vue'
import tags from '../components/Tags.vue'
let id = 0
export default{
	data(){
		return{
			items:[],
			filter:"all"
		}
	},
	components:{
		item,
		tags
	},
	methods:{
		addItem(e){
			if(e.target.value.trim()){
				this.items.unshift({
					id:id++,
					content:e.target.value,
					completed:false
				})
			}
			e.target.value = ""
		},
		completed:function(id){
			this.$set(this.items.find(item => item.id === id), 'completed', this.items.find(item => item.id === id).completed ? false : true)
		},
		del:function(id){
			this.items.splice(this.items.findIndex(item => item.id === id), 1)
		},
		filterToggle(state){
			this.filter = state
		},
		clear(){
			this.items = this.items.filter(item => item.completed === false);
		}
	},
	computed:{
		itemsFilter(){
			if(this.filter === 'all'){
				return this.items
			}
			const completed = this.filter === 'completed' ? true : false
			return this.items.filter(item => item.completed === completed)
		}
	}
}
</script>

<style type="text/css">
#todo{
	padding-top: 20px;
}
#todo input{
	width: 80%;
	height: 45px;
	max-width: 500px;
	font-size: 25px;
	border-radius: 5px;
}
</style>