<template>
 
  <div class="block">
    <span class="demonstration">带快捷选项</span>
    <el-date-picker
      v-model="value4"
      type="datetimerange"
      :picker-options="pickerOptions2"
      range-separator="至"
      start-placeholder="开始日期"
      end-placeholder="结束日期"
      v-if='flag'
      align="right">
    </el-date-picker>
    {{s}}
    <el-input type='text' v-model='s' v-if='!flag' @focus="flag=!flag">

    </el-input>
  </div>
</template>

<script>
  export default {
    data() {
      var _this=this
      return {
        s:'1',
        flag:true,
        pickerOptions2: {
          shortcuts: [{
            text: '最近一周',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              console.log(_this.flag)
              _this.flag=false
              _this.s='最近一周'
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近一个月',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近三个月',
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
              picker.$emit('pick', [start, end]);
            }
          }]
        },
        value3: [new Date(2000, 10, 10, 10, 10), new Date(2000, 10, 11, 10, 10)],
        value4: ''
      };
    }
  };
</script>