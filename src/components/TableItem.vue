<template>  
  <table>
      <div v-if="!edit">
            <tr>
                <td> {{title}} </td>
                <td> {{price}} </td>
                <td> {{quantity}} </td>
                <td> <button @click="Edit">X</button><button @click="Edit">Edit</button> </td>
            </tr>
      </div>
      <div v-if="edit">
        <input type="text" v-model="title">
        <input type="number" v-model="price">
        <input type="number" v-model="quantity">
        <button @click="Save">Save</button>
      </div>
  </table>
</template>

<script>
export default {
    props: ["table"],
    data() {
        return {
            title: this.table.title,
            price: this.table.price,
            quantity: this.table.quantity,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit("selected-title-changed", {
                original: this.table,
                new: {
                    title: this.title
                },
            }),
            this.$emit("selected-price-changed", {
                original: this.table,
                new: {
                    price: this.price
                },
            })
            this.$emit("selected-quantity-changed", {
                original: this.table,
                new: {
                    quantity: this.quantity
                },
            })
        }
    }
}
</script>
