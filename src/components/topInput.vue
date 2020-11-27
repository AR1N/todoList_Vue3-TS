<template>
    <div class="hello">
        <h1>{{tit}}</h1>
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
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
    name: "topInput",
    props: {
        tit: String,
    },
    setup() {
        return {
            inputVal: ref(""),
        };
    },
    methods:{
        onAdd(){
            if(!this.inputVal){
                return
            }
            this.$emit('on-add',this.inputVal)
            this.inputVal = ''
        }
    }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flex-align {
    display: flex;
    align-items: center;
}
</style>
