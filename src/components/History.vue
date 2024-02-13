<script setup>
    import { defineProps, ref } from 'vue';
    
    const emit = defineEmits(['transaction_delete'])

    const props = defineProps({
        transactions: {
            type: Array,
            required: true
        }
    });

    let transactionsCopy = ref(props.transactions.slice()); // Criando uma cópia do array de transações

    const delete_history = (id) =>{
        emit('transaction_delete', id)
    }

</script>

<template>
    <h3 class="container">History</h3>
    <section class="container">
        <div v-for="item in transactions" :key="item.id" @click="delete_history(item.id)">
            <p>{{ item.text }}</p>
            <p>$ {{ item.value }}</p>
            <p :class="item.value < 0 ? 'mines' : 'color'"></p>
        </div>
    </section>
</template>

<style scoped>

    h3{
        color: rgb(142, 18, 177);
    }

    div{
        display: flex;
        margin-top: 1rem;
        column-gap: 70px;
        align-items: center;
        text-align: center;
        border: 1px solid black;
        max-width: 300px;
        justify-content: center;
        border-radius: 5px ;
    }

  .mines{
    background-color: brown;
    width: 8px;
    height: 20px;
    border-radius: 3px;
    margin-top: 16px;
    }

  .color{
        background-color: rgb(50, 182, 50);
        width: 8px;
        height: 20px;
        border-radius: 3px;
        margin-top: 16px;
    }

    div:hover{
        background-color: rgb(169, 73, 73);
        cursor: pointer;
    }

</style>
