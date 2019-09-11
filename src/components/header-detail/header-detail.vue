<template>
	<div class="header-detail">
		<span v-show="visible">
			header-detail
			<span @click="hide()" style="color: red;">×</span>
		</span>
		
	</div>
</template>
<script>
	export default {
	  name: "header-detail",
	  props: {
	  },
	  data(){
		  return{
			  visible:false
		  }
	  },
	  methods:{
		  show(){
			  this.visible = true
		  },
		  hide(){
			  this.visible = false
		  }
	  }
	};
</script>
<style lang="stylus">
	
	
</style>