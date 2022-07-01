<template>
  <div>
    <ul>
      <li v-for="(item,index) in arr" :key="item">
      <span>{{item}}</span>
      <button @click="delFn(index)">删除</button>
      </li>
    </ul>
    <button @click="addFn">生成</button>
  </div>
</template>

<script>
export default {
  data(){
    return{
      arr:[1,5,3]
    }
  },
  methods:{
    addFn(){
      this.arr.push(Math.floor(Math.random() * 100));
    },
    delFn(index){
      this.arr.splice(index,1);
    }
  }
}
</script>

<style>

</style>