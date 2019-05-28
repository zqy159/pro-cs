<template>
    <el-button type="primary" @click="exportExcel()">
        <slot name='title'></slot>
    </el-button>
</template>

<script>
import {downExcel} from "./file"
export default {
    props:{
        data:Object,
    },
    name:"in-export",
    methods:{
        exportExcel(){
            downExcel(this.data)
        }
    },
    mounted(){
        // console.log(this.data)
    }

}
</script>

