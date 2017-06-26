# vue2-select

> A Vue.js project
 
### 功能
提供类似ui-select一样的多功能选择框，提供搜索、多选、选择全部等功能

### demo使用方法 
```
git clone https://github.com/wmy1992/vue2-select.git
cd vue2-select
npm install
npm run dev
```
### 使用方法：
提取components中的vue-select到自己项目中，具体使用方法见示例App.vue



> 父组件需要子组件选中的选项，可以通过给子组件添加索引ref，获取子组件的checkitems
>$refs 只在组件渲染完成后才填充，并且它是非响应式的。它仅仅作为一个直接访问子组件的应急方案——应当避免在模版或计算属性中使用 $refs.
