<script setup>

    import {ref} from 'vue'
    import {useToast} from 'vue-toastification'

    const text = ref('')
    const amount = ref('')
    const toast = useToast()

    const emit = defineEmits(['newTransaction'])

    const newCost = () => {
        if(!text.value || !amount.value){
            toast.error('os campos precisam ser preenchidos !')
        }
        
        const data =  {
            text : text.value,
            amount : amount.value
        }

        emit('newTransaction', data)
        
        text.value = ''
        amount.value = ''
    }

</script>

<template>
    
    <h3 class="container">Add new transition</h3>
    <form class="container" @submit.prevent="newCost">
        <div class="mb-3 col-5 ">
            <label for="exampleInputEmail1" class="form-label">Text</label>
            <input type="text" v-model="text" class="form-control form" id="exampleInputEmail1" aria-describedby="emailHelp">
            <div id="emailHelp" class="form-text">Write anything...</div>
        </div>
        <div class="mb-3 col-5">
            <label for="exampleInputPassword1"  class="form-label">Value</label>
            <input type="number" class="form-control form" v-model="amount" id="exampleInputPassword1">
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>

</template>

<style scoped>

    h3{
        margin-top: 3rem;
        color:  rgb(142, 18, 177);
    }

    .form{
        border: 1px solid black;
    }

</style>