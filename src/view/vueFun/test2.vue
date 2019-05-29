<template>
        <div>
            <el-form :model="numberValidateForm" ref="numberValidateForm" label-width="100px" class="demo-ruleForm">
  <el-form-item
    label="年龄"
    prop="age"
    :rules="m || k?rules.age:null"
  >
    <el-input type="age" v-model.number="numberValidateForm.age" autocomplete="off"></el-input>
  </el-form-item>
  <el-form-item>
    <el-button type="primary" @click="submitForm('numberValidateForm')">提交</el-button>
    <el-button @click="resetForm">重置</el-button>
  </el-form-item>
</el-form>

            <el-button type="text" @click="dialogVisible = true">点击打开 Dialog</el-button>
<div style="width:500px;position:absolute;overflow:hidden;border:1px solid #f00">
    <el-dialog
  title="提示"
  :visible.sync="dialogVisible"
  width="30%"
  :before-close="handleClose">
  <p style="height:500px">这是一段信息</p>
 <!-- <p style="height:500px">这是一段信息</p>
 <p style="height:500px">这是一段信息</p>
 <p style="height:500px">这是一段信息</p>
 <p style="height:500px">这是一段信息</p> -->
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
  </span>
</el-dialog>
</div>

        </div>


</template>


<script>
  export default {
    data() {
      return {
        numberValidateForm: {
          age: ''
        },
        dialogVisible:false,
        k:false,
        m:true,
        rules:{
            age:{ required: true, message: '请输入邮箱地址', trigger: 'blur' },
        }
      };
    },
    methods: {
        handleClose(){
            this.dialogVisible = false
        },
      submitForm(formName) {
        this.m=false
        this.$refs[formName].validate((valid) => {
        console.log(valid)
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
          this.k=true
      }
    }
  }
</script>

<style>
@keyframes myfirst
{
from {right:-300px;}
to {right: 0px;}
}
.el-dialog__wrapper{
        overflow-x: hidden;
}
.el-dialog{
    float: right;
    min-height:100%;
    overflow: hidden;
    margin:0 !important;
    animation:myfirst 1s;
}
</style>
