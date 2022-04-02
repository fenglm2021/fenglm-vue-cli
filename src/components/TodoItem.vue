<!--这里写的是html代码 -->
<template>
    <li class="item">
        <!-- checkbox复选框 -->
        <input type="checkbox" v-model="yuan" >
           
        <!-- slot是vue中的插槽，插槽用于决定将所携带的内容，插入到指定的某个位置 -->
        <!-- 通过插槽jialin将checkbox选中状态（true或false）checked值传递过去，在App.vue的中使用了插槽v-slot:jialin -->
        <slot name="jialin" v-bind="{yuan}"></slot>
    </li>
</template>

<!--这里写的是js代码 -->
<script>
export default {
    props:['item'],
    data(){
        return{
            // isCheck和<input type="checkbox" v-model="isCheck">中的v-model进行双向绑定
            yuan:false,
        }
    }
}
</script>

<!--这里写的是css代码，加上scoped属性表示：style里面所写的css样式只会对本文件中<template>模板中的html代码生效，别的地方用是不好使的 -->
<style scoped>
 .item {
     color: red;
 }
</style>

