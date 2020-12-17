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
            <div class="sub-button" @click="onAdd">添加</div>
        </div>
        <div style="margin-top: 50px">
            <div class="item" v-for="(item, index) in todo" :key="index">
                {{ item }}
                <span
                    class="el-icon-circle-close del"
                    @click="onDel(index)"
                ></span>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref, toRefs } from "vue";

export default defineComponent({
    name: "App",
    setup() {
        let inputVal = ref("");
        let list: any[string] = reactive({
            todo: ["hello vue3 !"],
        });
        function onDel(index: number) {
            list.todo.splice(index, 1);
        }
        function onAdd() {
            if (!inputVal.value) return;
            list.todo.unshift(inputVal.value);
            inputVal.value = "";
        }
        return {
            ...toRefs(list),
            onDel,
            onAdd,
            inputVal,
        };
    },
});
</script>

<style >
html,
body {
    background-color: #ebf3fa;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.root {
    max-width: 740px;
    margin: 50px auto;
}
 .el-input /deep/ .el-input__inner{
 box-shadow: inset 3px 3px 5px 2px #c4d0db, inset -3px -3px 5px 2px #fff;
}
.el-input__inner:focus{
  border: none;
  outline: none;
}
.flex-align {
    display: flex;
    align-items: center;
}
.sub-button {
    color: #409eff;
    font-weight: bold;
    padding: 8px 30px;
    margin-left: 20px;
    white-space: nowrap;
    background: #e6edf7;
    cursor: pointer;
    box-sizing: border-box;
    user-select: none;
    border-radius: 5px;
    border: 1px solid transparent;
    box-shadow: 3px 3px 5px 3px #c4d0db, -3px -3px 5px 2px #fff;
}
.sub-button:active {
    box-shadow: inset 3px 3px 5px 2px #c4d0db, inset -3px -3px 5px 2px #fff;
    border: 1px solid #fff;
}
.item {
    position: relative;
    color: #41b883;
    font-weight: bold;
    padding: 20px 60px 20px;
    border-radius: 10px;
    margin-bottom: 20px;
    word-break: break-all;
    background-color: #e6edf7;
    box-shadow: 0 3px 5px 3px #c4d0db, 0 -3px 5px 2px #fff;
}
.item:hover{
  background-color:#f3f8ff;
}
.del {
    position: absolute;
    right: 20px;
    top: 20px;
    font-size: 20px;
    color: red;
    cursor: pointer;
}
</style>


