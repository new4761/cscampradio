<template>

<el-row style="font-family: 'Sarabun', sans-serif;">
  <el-col :span="4" v-for="(run,i)  in info" :key="i" ><div class="grid-content bg-purple">  <el-col :span="4"><div class="grid-content bg-purple-light"><el-card class="box-card" >
  <div slot="header" class="clearfix radius-2">
    <span  style="text-align: center; font-size:3em;">กลุ่มที่ : {{run[0]}}</span>
  </div>
  <div v-for="o in 6" :key="o" class="text item" style=" background:#fffffF;">
      <p
        v-if="o==6" style="text-align: center; font-size:3em;">{{run[o]}}</p>
    <p    v-else>กิจกรรมที่ {{o}} =>{{run[o]}}</p>   
  </div>
</el-card></div></el-col></div></el-col>

</el-row>

 
</template>

<script>
import Logo from '~/components/Logo.vue';
import axios from "axios";
export default {
  data() {
    return {
info: null
    };
  },
 mounted() {
     axios.get('https://sheets.googleapis.com/v4/spreadsheets/13zOsEonZZY57gbOE0N-0O0UpofhSivuRgCUGE56BfIo/values/A1:H25?key=AIzaSyBFD5yNQVy4MqdnGjd4Bz2oRDZmSAD2HUM')
      .then(response => (this.info = response.data.values));
  }
};
  
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Sarabun&display=swap');
.links {
  padding-top: 15px;
}

  .text {
    font-size: 18px;
  }

  .item {
    margin-bottom: 18px;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  .box-card {
    width: 350px;
  }
    .el-row {
    margin-bottom: 20px;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background:   #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }

</style>
