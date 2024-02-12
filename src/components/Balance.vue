<script setup>
    import { defineProps } from 'vue';

    const total = defineProps({
        total : {
            type : Number,
            required : true
        }
    })

</script>

<template>
    <div class="container">
        <h2>
            YOUR BALANCE 
        </h2>
    
        <p>$ {{ total }}</p>
    </div>
</template>

<style scoped>

    .container{
        margin-top: 2rem;
    }

</style>