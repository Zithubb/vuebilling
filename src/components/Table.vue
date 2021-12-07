<template>
   <div>
      <table>
         <thead>
            <tr>
                <th>Név</th>
                <th>Ár</th>
                <th>Darabszám</th>
                <th>Operations</th>
            </tr>
         </thead>
         <tbody>
            <TableItem
               v-for="table in tables"
               v-bind:key="table.title"
               :table="table"
               @selected-table-changed="Changed"
               @selected-item-delete="Delete"
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
            this.$emit("selected-title-changed", e)
            this.$emit("selected-prive-changed", e)
            this.$emit("selected-quantity-changed", e)
         },
         Delete(e){
               this.$emit('raktar-item-delete', e)
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
 