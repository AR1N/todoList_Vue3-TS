<template>
    <div class="root">
        <img alt="Vue logo" src="./assets/logo.png" />
        <h1>vue3.0+ts</h1>
        <div class="flex-align">
            <el-input
                placeholder="请输入内容"
                prefix-icon="el-icon-edit"
                v-model="inputVal"
                clearable
            >
            </el-input>
            <el-button type='primary' style="margin-left:20px;width:100px" @click="onAdd">添加</el-button>
        </div>
        <div style="margin-top:50px">
          <div class="item" v-for="(item,index) in todo" :key="index">{{item}} <span class="el-icon-circle-close del" @click="onDel(index)"></span> </div>
        </div> 
    </div>
</template>

<script lang="ts">
import { defineComponent,reactive,ref,toRefs } from "vue";

export default defineComponent({
    name: "App",
    setup(){
        let inputVal = ref('')
        let list:any[string] = reactive({
          todo:['hello vue3 !']
        })
      function onDel(index:number){
        list.todo.splice(index,1)
      }
      function onAdd(){
        if( !inputVal.value)return
       list.todo.unshift(inputVal.value)
       inputVal.value = ''
      }
      return {
        ...toRefs(list),
        onDel,
        onAdd,
        inputVal
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
.flex-align {
    display: flex;
    align-items: center;
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


