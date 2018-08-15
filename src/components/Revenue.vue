<template>
  <div class="container is-fluid">
    <h2 class="title is-2">Revenue</h2>
    <div class="button is-primary">
      <router-link :to="{name: 'AddRevenue'}">
        Add Record
      </router-link>
    </div>
    <div>
      <b-table :data="data" :columns="columns"></b-table>

    <el-table
    :data="data"
    style="width: 100%"
    height="250">
    <el-table-column
      v-for="(column, index) in columns"
      :key="index"
      :prop="column.field"
      :label="column.label"
      width="120">
    </el-table-column>
  </el-table>


    </div>
  </div>
</template>

<script>
import db from '@/firebase/init'
export default {
  name: 'Revenue',
  data () {
    return {
      data: [],
      columns: [
        {
          field: 'date',
          label: 'Date'
        },
        {
          field: 'invoiceId',
          label: 'Invoice ID'
        },
        {
          field: 'clientName',
          label: 'Client name'
        },
        {
          field: 'description',
          label: 'Description'
        },
        {
          field: 'amount',
          label: 'Amount',
          numeric: true
        }
      ]
    }
  },
  created () {
// fetch data from firestore
  db.collection('revenue').get()
  .then(snapshot => {
    snapshot.forEach(doc => {
      let revenue = doc.data()
      revenue.id = doc.id
      this.data.push(revenue)
      })
    })
  }
}
</script>

<style scoped>
.container h2{
  padding-top: 25px;
}
.button{
  position: fixed;
  top: 120px;
  right: 75px;
}
</style>
