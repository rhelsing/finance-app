<template>
 <div class="add-revenue container is-fluid">
   <h2 class="title is-2">Add New Revenue Record</h2>
   <el-form @submit="addRevenue" ref="form" label-width="120px">
      <el-form-item v-for="(c, index) in columns" :key="index" :label="c.label">
        <el-date-picker v-if="c.type == 'date'" type="date" placeholder="Pick a date" v-model="c.field" style="width: 100%;"></el-date-picker>
        <el-input v-else-if="c.type == 'text'" v-model="c.field"></el-input>
      </el-form-item>
      <button class="button is-success">Add Record</button>
   </el-form>

 </div>
</template>

<script>
import db from '@/firebase/init'
// import slugify from 'slugify'
export default {
  name: 'AddRevenue',
  data () {
    return {
      columns: {
        date: {label: 'Date', field: null, type: 'date'},
        invoiceId: {label: 'Invoice ID', field: null, type: 'text'},
        clientName: {label: 'Client name', field: null, type: 'text'},
        description: {label: 'Description', field: null, type: 'text'},
        amount: {label: 'Amount', field: null, type: 'text'}
      },
      feedback: null,
    }
  },
  methods: {
    addRevenue() {
      console.log(this.columns)
      db.collection('revenue').add({
        date: this.columns.date.field,
        invoiceId: this.columns.invoiceId.field,
        clientName: this.columns.clientName.field,
        description: this.columns.description.field,
        amount: this.columns.amount.field
      }).then(() => {
        this.$router.push({name: 'Revenue'})
      }).catch(err => {
        console.log(err)
      })

  //
    // create slug
  //       this.slug = slugify(this.title, {
  //         replacement: '-',
  //         remove: /[$*_+~.()'"!\-:@]/g,
  //         lower: true
  //       })
  //       db.collection('smoothies').add({
  //         title: this.title,
  //         ingredients: this.ingredients,
  //         slug: this.slug
  //       }).then(() => {
  //         this.$router.push({name: 'Index'})
  //       }).catch(err => {
  //         console.log(err)
  //       })
  //   },
  //   addIng() {
  //     if(this.another){
  //       this.ingredients.push(this.another)
  //       this.another = null
  //       this.feedback = null
  //     } else {
  //       this.feedback = "You must enter a value to add an ingredient"
  //     }
  //   },
  //   deleteIng(ing) {
  //     this.ingredients = this.ingredients.filter(ingredient => {
  //       return ingredient != ing
  //       })
  //   }
    }
  }
}
</script>


<style scoped>
.container{
  position: fixed;
  max-width: 500px;
  margin: 50px;
}
</style>
