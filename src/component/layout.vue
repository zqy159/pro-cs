<template>
    <div class="layout" v-if="$store.getters.username">
         <!-- <Header /> -->
        <div class="content">
            <div style="float:left" :class="r?'left1':'left2'">
                  <!-- <Navigation />  -->
            </div>
            <div style="float:left">
                <!-- <NavBreadcrumb />   -->
                    <router-view />
            </div>
            <!-- <el-row>
                <el-col :span="leftWidth">
                    <Navigation /> 
                </el-col>
                <el-col :span="rightWidth">
                    <NavBreadcrumb />  
                    <router-view />
                </el-col>
            </el-row> -->
        </div>  
        
    </div>
    <div class="layout" v-else>
        <router-view />
    </div>
</template>

<script>
import Navigation from "./public/Navigation";
import Header from "./public/Header";
import NavBreadcrumb from "./public/NavBreadcrumb";
export default {
  name: "Layout",
  components: {
    Navigation,
    Header,
    NavBreadcrumb
  },
  data(){
    return{
        leftWidth:3,
        r:true,
        rightWidth:21,
    }
  },
  mounted() {
      this.$center.$on("isCollapse",(r)=>{
          if(r){
              this.r=flase
          }else{
               this.r=true
          }
      })
  }
};
</script>
<style lang="scss">
// .left1{
//     width:200px;
// }
// .left2{
//     width:64px;
// }
.layout {
  height: 100%;
  .content {
    height: 90%;
  }
  .el-row,.el-col{
    overflow: auto;
    height: 100%!important;
    .el-menu-item{
      min-width:100%!important;
    }
  }
}
</style>


