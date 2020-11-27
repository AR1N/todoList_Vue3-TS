<template>
    <div class="root">
        <img alt="Vue logo" src="./assets/logo.png" />
        <TopInput tit='vue3.0+ts' @onAdd='addData'/>
        <div style="margin-top:50px">
          <div class="item" v-for="(item,index) in todo" :key="index">{{item}} <span class="el-icon-circle-close del" @click="onDel(index)"></span> </div>
        </div> 
    </div>
</template>

<script lang="ts">
import { defineComponent,reactive,toRefs } from "vue";
import TopInput from "./components/topInput.vue";

export default defineComponent({
    name: "App",
    components: {
        TopInput
    },
    setup(){
        let list:any[string] = reactive({
          todo:[]
        })
      function onDel(index:number){
        list.todo.splice(index,1)
      }
      function addData(data:any){
       list.todo.unshift(data)
      }
      return {
        ...toRefs(list),
        onDel,
        addData
      }
    }
});
</script>

<style >
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.root{
 max-width: 740px;
 margin:50px auto;
}
.item{
  position: relative;
  color: #41b883;
  font-weight: bold;
  padding: 20px 60px 20px;
  border-radius: 10px;
  margin-bottom: 15px;
word-break: break-all;
  background-color: #fff;
  box-shadow: 0 5px 10px #35495e;
}
.del{
  position: absolute;
  right: 20px;
  top: 20px;
  font-size: 20px;
  color: red;
  cursor: pointer;
}
</style>


