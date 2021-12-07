<template>  
        <tr>
            <td v-if="!edit"> {{title}} </td>
            <td v-if="!edit"> {{price}} </td>
            <td v-if="!edit"> {{quantity}} </td>
            <td v-if="!edit"> <button @click="Delete">X</button><button @click="Edit">Edit</button> </td>
            <td v-if="!edit">{{quantity*price}}</td>
        
            <td v-if="edit"><input type="text" v-model="title"></td>
            <td v-if="edit"><input type="number" v-model="price"></td>
            <td v-if="edit"><input type="number" v-model="quantity"></td>
            <td v-if="edit"><button @click="Save">Save</button></td>
            
        </tr>
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
            this.$emit('table-item-changed', {
                original: this.raktar,
                new: {
                    title: this.title,
                    price:this.price,
                    quantity:this.quantity
                    },
            })
        },
        Delete(){
            this.$emit('table-item-delete',{
                original:this.table
            })
        }
    }
}
</script>
