<template>
	<div id="vue-select-container" class="vue-select-container">
		<span class="vue-checked-num" @click="displaySelect=!displaySelect">{{checkitems.length}} checked <i :class="[displaySelect?'down-triangle':'up-triangle']"></i></span>
		<ul class="vue-select" :class="{'vue-select-display':!displaySelect}">
			<ul class="vue-operate">
				<li class="checked-all" @click='checkall(true)'>&#10003 check all</li>
				<li class="unchecked" @click='checkall(false)'>&#10006 uncheck all</li>
			</ul>
			<li class="vue-search"><input type="text"  v-model="filterText" autofocus="autofocus" placeholder="search"></li>
			<li v-for="item in filterLists" @click="selectItem(item)"><label for="" class="vue-check-mark" :class="{'check-mark':item.unchecked||item.unchecked===undefined}">&#10003 </label>{{item.value}}</li>
		</ul>
	</div>
</template>

<script type="text/javascript">
	export default{
		props:['selectLists'],
		data(){
			return {
				//checknames:[],
				filterText:'',
				displaySelect:false,
				//checkedNum:0
			}
		},
		computed:{
			filterLists:function(){
				if(this.filterText.trim().length==0){
					return this.selectLists;
				}
				return this.selectLists.filter(item=>{
					return item.value.indexOf(this.filterText)>-1
				});
			},
			checkitems:function(){
				return this.filterLists.filter(item=>{
					return item.unchecked===false
				});
			}

		},
		methods:{
			selectItem:function(item){
				if(item.unchecked===undefined){ 
					this.$set(item,'unchecked',false);
				}else{						
					item.unchecked=!item.unchecked;
				}
			},
			checkall:function(flag){
				if(flag){
					this.filterLists.forEach(item=>{
						if(item.unchecked===undefined){
							this.$set(item,'unchecked',false);
						}else{
							item.unchecked=false;
						}
					})
				}else{
					 this.filterLists.forEach(item=>{
						if(item.unchecked===undefined){
							this.$set(item,'unchecked',true);
						}else{
							item.unchecked=true;
						}
					})
				}
			}
		}
	}
</script>

<style type="text/css">
		*{
	    	padding:0;
	    	margin:0;
	    }

		.vue-select-container{
			position:relative;
			display:inline-block;
			
		}
		 
		.vue-select{
			width:160px;
			height:300px;
			list-style:none;
			border:1px solid #ccc; 
			position:absolute;
			overflow-y:scroll;

		}

		.vue-select-display{
			display:none;
		}
		.vue-select-container span.vue-checked-num{
			display:inline-block;
			width:140px;
			height:30px;
			line-height:30px;
			margin-bottom:5px;
			border:1px solid #ccc;
			padding-left:8px;
			position:relative;
		}

		.vue-select-container i.up-triangle{
			content:"";
			width:0;
			height:0;
			position:absolute;
			top:12px;
			right:20px;
		    border-top:none;
			border-left:5px solid transparent;
			border-right:5px solid transparent;
			border-bottom:8px solid #aaa;
		}
		
		.vue-select-container i.down-triangle{
			content:"";
			width:0;
			height:0;
			position:absolute;
			top:12px;
			right:20px;
		    border-bottom:none;
			border-left:5px solid transparent;
			border-right:5px solid transparent;
			border-top:8px solid #aaa;
		}
		.vue-select li.vue-checked-num:focus{
			outline:1px solid #f00;
		}

		ul.vue-select li:hover{
			background:#ddd;
			cursor:pointer;
		}

		.vue-select ul.vue-operate{
			width:100%;
			list-style:none;
			border:none;
			border-bottom:1px solid #ccc;
		}

		.vue-select li{
			border-top:none;
			border-bottom:none;
			height:30px;
			margin:10px;
			line-height:30px;
			/*border-left:1px solid #ccc;
			border-right:1px solid #ccc;*/
		}
		.vue-select li.vue-search{
			border-bottom:1px solid #ccc;
			z-index:100;
		}
		.vue-select li.vue-search input{
			box-sizing:border-box;
			width:100%;
			border:1px solid #ccc;
			height:100%;
			z-index:101;
			padding-left:10px;
		}

		.vue-select li.search input:focus{
			outline:#00f solid 1px;
		}

		.vue-select label.check-mark{
			display:none;
		}

		.vue-select label.vue-check-mark{
			color:#f00;
			padding-right:5px;
			font-weight:bold;
		}
</style>