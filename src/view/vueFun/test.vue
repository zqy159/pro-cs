<template>
  <div>
    <el-select v-model="value" multiple filterable remote reserve-keyword placeholder="请输入关键词" :remote-method="remoteMethod" :loading="loading">
      <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value">
      </el-option>
    </el-select>
    <div>
      <el-tag v-for="(tag,index) in tags" :key="tag" closable type="info"  @close="handleClose(index)">
        {{tag}}
      </el-tag>

    </div>
    <el-popover placement="bottom" width="220" trigger="click">
      <div class="box">
        <li v-for="(item,index) in option" :key="item.value" style="cursor:pointer;height:" @click='clickSelect(item,index)'>

          <i class="el-icon-check" style="margin-right:10px;color:#409EFF" v-show='item.disabled'></i>{{item.label}}
        </li>
      </div>
      <el-input placeholder="请输入内容" prefix-icon="el-icon-search" v-model="searchInput" slot="reference" style="width:250px" @input='getSearch'>
      </el-input>
    </el-popover>
  </div>

</template>

<script>
export default {
  data() {
    return {
      tags: [],
      searchInput: '',
      options: [],
      selectOptions: [],
      option: [],
      value: [],
      list: [],
      loading: false,
      states: ["Alabama", "Alaska", "Arizona",
        "Arkansas", "California", "Colorado",
        "Connecticut", "Delaware", "Florida",
        "Georgia", "Hawaii", "Idaho", "Illinois",
        "Indiana", "Iowa", "Kansas", "Kentucky",
        "Louisiana", "Maine", "Maryland",
        "Massachusetts", "Michigan", "Minnesota",
        "Mississippi", "Missouri", "Montana",
        "Nebraska", "Nevada", "New Hampshire",
        "New Jersey", "New Mexico", "New York",
        "North Carolina", "North Dakota", "Ohio",
        "Oklahoma", "Oregon", "Pennsylvania",
        "Rhode Island", "South Carolina",
        "South Dakota", "Tennessee", "Texas",
        "Utah", "Vermont", "Virginia",
        "Washington", "West Virginia", "Wisconsin",
        "Wyoming"]
    }
  },
  mounted() {
    this.getSearch()
    this.list = this.states.map(item => {
      return { value: item, label: item };
    });
  },
  methods: {
    handleClose(index){
     this.tags.splice(index,1)
     this.option.forEach((items,i) => {
        if (this.tags.includes(items.value)) {
           this.option[i].disabled=true
        } else {
           this.option[i].disabled=false
        }
      })
    },
    clickSelect(val,index) {
      console.log(index)
      if(this.tags.includes(val.value)){
        this.tags.splice(this.tags.find((item)=>{
          return item.value
        }),1)
      }else{
        this.tags.push(val.value)
      }
   
      this.option.forEach((items,i) => {
        if (this.tags.includes(items.value)) {
           this.option[i].disabled=true
        } else {
           this.option[i].disabled=false
        }
      })

    },
    getSearch() {

      this.option = this.states.filter(item => {
        return item.includes(this.searchInput)
      }).slice(0, 20).map(items => {
        if (this.tags.includes(items.value)) {
          return { value: items, label: items, disabled: true };
        } else {
          return { value: items, label: items, disabled: false };
        }

      })
      console.log()
    },
    remoteMethod(query) {
      if (query !== '') {
        this.loading = true;
        setTimeout(() => {
          this.loading = false;
          this.options = this.list.filter(item => {
            return item.label.toLowerCase()
              .indexOf(query.toLowerCase()) > -1;
          });
        }, 200);
      } else {
        this.options = [];
      }
    }
  }
}
</script>

<style <style lang="scss">
.box {
  height: 220px;
  overflow-y: auto;
  li {
    width: 215px;
    font-size: 14px;
    // padding: 0 20px;
    cursor: pointer;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    color: #606266;
    height: 34px;
    line-height: 34px;
  }
  li:hover {
    background: #f5f7fa;
  }
}
</style>

