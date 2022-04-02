<!--这里写的是html代码 -->
<template>
  <div id="app">
    {{msg}}
    <!-- div代码块-start -->
    <div>
      <!-- input输入框，输入的内容会赋值给info -->
      <input type="text" v-model="info">
      <!-- button添加按钮，鼠标单击事件（v-on:click）中定义了一个handleClick方法 -->
      <button ref="inputPosition" v-on:click="handleClick">添加</button>
    </div>
    <!-- div代码块-end -->

    <!-- ul代码块-start -->
    <ul>
       <!-- 通过v-for循环获取list数组中的内容，每次获取内容以item变量输出 -->
       <todo-item v-for="flm in list" :key="flm">
         <!-- 通过v-slot:jialin插槽传递checkbox是否选中的对象,选中时itemProps.checked=true，未选中时itemProps.checked=false -->
         <template v-slot:jialin="itemProps">
           <!-- {{flm}}获取循环的内容 -->
           <span :style="{fontSize:'20px',color:itemProps.yuan?'red':'blue'}">{{flm}}</span>
         </template>
       </todo-item>
    </ul>
    <!-- ul代码块-end -->
  </div>
</template>

<!--这里写的是js代码 -->
<script>
// 引用TodoItem组件
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'app',
  //在这里初始化数据
  data(){
    return{
      msg:'单文件组件',
      info:'',
      list:[],
    }
  },

  //在这里编写方法
  methods:{
    //button按钮的单击事件方法
    handleClick(){
      if(this.info==''){
        alert("请先写点啥呗")
        return;
      }

      //向list数组中添加input框中输入的info内容
      this.list.push(this.info)
      //清空input框中输入的info内容
      this.info = ''
    }
  },

  //在这里注册组件
  components: {
    TodoItem,
  }
}
</script>

<!--这里写的是css代码 -->
<style>

</style>
