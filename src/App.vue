<template>
  <div id="app">
    <h1></h1>
    <h2>vue-select</h2>

    <!-- 使用组件vue-select，传递lists对象给子组件，指定ref用于父组件访问子组件中的值 -->
    <vue-select ref="vueSelect" :selectLists="lists" ></vue-select>
    <button @click="getSelected">选择项</button>
     
     
  </div>
</template>

<script>

// 引入组件vue-select
import vueSelect from  './components/vue-select.vue'

export default {
  name: 'app',
  data () {
    return {
       lists:[
        {id:'1',value:'vue组件'},
        {id:'2',value:'学习写select'},
        {id:'3',value:'实现下拉列表'},
        {id:'4',value:'可以搜索'},
        {id:'5',value:'类似ui-select'},
      ]
    }
  },
  methods:{
    getSelected(){
      console.log(this.$refs.vueSelect.checkitems);
    }
  },
  // computed:{
  //   selected(){
  //     console.log(this.$refs);
  //     return this.$refs.vueSelect.checkitems;
  //   }
  // },
  components:{
    vueSelect,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  margin:20px 30px;
}

</style>
