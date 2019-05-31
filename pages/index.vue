<template>

<el-row>
  <el-col :span="4" v-for="(run,i)  in info" :key="i"><div class="grid-content bg-purple">  <el-col :span="4"><div class="grid-content bg-purple-light"><el-card class="box-card">
  <div slot="header" class="clearfix">
    <span>{{ run[0]  }}</span>
    <el-button style="float: right; padding: 3px 0" type="text">Operation button</el-button>
  </div>
  <div v-for="o in 6" :key="o" class="text item">
      <p
        v-if="o==6">คะเเนนรวม =>{{run[o]}}</p>
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

.links {
  padding-top: 15px;
}

  .text {
    font-size: 14px;
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
    width: 480px;
  }
    .el-row {
    margin-bottom: 20px;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
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
