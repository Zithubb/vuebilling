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
               />
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
         }
      }
   }
</script>
 