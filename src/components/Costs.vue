<script setup>

    import { defineProps } from 'vue';

    const props = defineProps({
        expense : {
            type : Number,
            required : true
        },

        income : {
            type : Number,
            required : true
        }
    })


</script>

<template>
    <section class="container d-flex justify-content-evenly col-5 flex-wrap">
        <div> 
            <h3>INCOME</h3>
            <p class="plus">+ $ {{ income }}</p>
        </div>


        <div>
            <h3>EXPENSE</h3>
            <p class="mines">- $ {{ expense }} </p>
        </div>
    </section>
</template>

<style scoped>

    section{
        box-shadow: 5px 5px 10px 0px rgba(0,0,0,0.5); /* Adiciona sombra na parte inferior e no lado direito */
        max-width: 400px;
        align-items: center;
        text-align: center;
        border-radius: 8px;
    }

.plus{
        color: rgb(50, 182, 50) ;
    }

    .mines{
        color: rgb(239, 51, 51);
    }

    span{
        background-color: rgb(125, 10, 157);
        width: 2px;
        height: 50px;
        margin-bottom: 10px;
        border-radius: 5px;
    }

    h3{
        color: rgb(142, 18, 177);
    }

</style>