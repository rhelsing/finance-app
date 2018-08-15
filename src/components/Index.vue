<template>

  <el-main>

    <el-row :gutter="20">

      <el-col :span="8">
        <el-card class="box-card clearfix" shadow="hover">
          <span class="title is-2">Revenue</span>
          <router-link :to="{name: 'Revenue'}"><el-button style="float: right;" icon="el-icon-search" circle></el-button></router-link>
        </el-card>
      </el-col>

      <el-col :span="8">
        <el-card class="box-card" shadow="hover">
          <div slot="header" class="clearfix">
            <span class="title is-2">Expenses</span>
          </div>
          <el-button :to="{name: 'Expenses'}" style="float: right; padding: 3px 0" type="text">Manage</el-button>
        </el-card>
      </el-col>

      <el-col :span="8">
        <el-card class="box-card" shadow="hover">
          <div slot="header" class="clearfix">
            <span class="title is-2">Recievables</span>
          </div>
          <el-button :to="{name: 'Expenses'}" style="float: right; padding: 3px 0" type="text">Manage</el-button>
        </el-card>
      </el-col>
    </el-row>


  </el-main>
</template>

<script>
import db from '@/firebase/init'
export default {
  name: 'Index',
  data () {
    return {

    }
  }
}
</script>

<style scoped >
.is-ancestor{
padding-right: 75px;
padding-left: 75px;
padding-top: 35px;
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
</style>
