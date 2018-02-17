<template>
	<div id="ahead">
		<p>{{title}}</p>
	</div>
</template>

<script type="text/javascript">
export default{
	data () {
		return {
			title: "Todo List"
		}
	}
}
</script>

<style type="text/css">
#ahead{
	width: 100%;
	height: 60px;
	background-color: #35495e;
	color: white;
	font-size: 35px;
	line-height: 60px;
}
</style>