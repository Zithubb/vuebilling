<template>
   <div>
      <table>
         <thead>
            <tr>
                <th>Név</th>
                <th>Ár</th>
                <th>Darabszám</th>
                <th>Operations</th>
                <th>Összérték</th>
            </tr>
         </thead>
         <tbody>
            <TableItem
               v-for="table in tables"
               v-bind:key="table.title"
               :table="table"
               @table-item-changed="Changed"
               @table-item-delete="Delete"
               />
            <tr>
               <td><input type="text" v-model="title"></td>
               <td><input type="number" v-model="price"></td>
               <td><input type="number" v-model="quantity"></td>
               <td><button @click="Post">Hozzáad</button></td>
            </tr>
         </tbody>
      </table>
   </div>  
</template>

<script>
   import TableItem from './TableItem.vue'
   export default {
      props: ['tables'],
      components: {TableItem},
      methods: {
         Changed(e) {
               this.$emit('table-item-changed', e)
         },
         Delete(e){
               this.$emit('table-item-delete', e)
         },
         Post(){
            this.$emit('table-item-post', {
                new:{
                    title:this.title,
                    price:this.price,
                    quantity:this.quantity
                }
            })
            this.title="",
            this.price=null,
            this.quantity=null
        }
      }
   }
</script>
 