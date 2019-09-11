<template>
  <div id="app">
	<div class="header">
		<v-header :seller="seller"></v-header>
	</div>
	
	
	<div class="tab-wrapper">
		<v-tab :tabs="tabs" :initialIndex='0' ></v-tab>
	</div>
	
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import VHeader from "components/header/header.vue"
import VTab from "components/tab/tab.vue"
import {getSeller} from "components/api/index.js"
import {getGoods} from "components/api/index.js"
import {getRatings} from "components/api/index.js"

import Goods from "components/goods/goods"
import Ratings from "components/ratings/ratings"
import Seller from "components/seller/seller"

export default {
	name: "app",
	data(){
		return{
			seller:{},
		} 
	},
	computed:{
		tabs(){
			return[
				{
					label:'主页',
					component:Goods,
					data:{seller:this.seller},
					icon:'cubeic-home',
				},
				{
					label:'商家',
					component:Seller,
					data:{seller:this.seller},
					icon:'cubeic-vip',
				},
				{	
					label:'评论',
					component:Ratings,
					data:{seller:this.seller},
					icon:'cubeic-person',
				},
				
				
				
			]
		},
		
	},
	created(){
		getSeller().then((seller)=>{
			this.seller = seller
			console.log(this.seller)
		})
	},  
	components: {
		// HelloWorld
		VHeader,
		VTab
	},
  
};
</script>

<style lang="stylus" scoped>
	#app
		.tab-wrapper
			position: fixed
			top: 136px
			left: 0
			right: 0
			bottom: 0
</style>
