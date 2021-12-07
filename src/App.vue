<template>
  <div id="app">
    <Table :tables="tables" @table-item-changed="Changed" @table-item-delete="Delete" @table-item-post="Post"/>
  </div>
</template>

<script>
import Table from './components/Table.vue'

export default {
  name: 'App',
  components: {
    Table
  },
  data() {
    return {
      tables: [
        {
          title: 'Kerék',
          price: 100,
          quantity: 12
        },
        {
          title: 'Teleszkóp',
          price: 1000,
          quantity: 300
        },
        {
          title: 'Kormány',
          price: 230,
          quantity: 5
        },
        {
          title: 'Ajtó',
          price: 45120,
          quantity: 321
        },
      ]
    }
  },
  methods:{
      Changed(e) {
      this.tables.map(function (table) {
        if (table.title != e.original.title) {
          return table
        }
        table.title = e.new.title
        return table
      })
    },
    Post(e){
      this.tables.push(e.new)
    },
    Delete(e){
      this.tables.splice(this.tables.indexOf(e.original), 1);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
