<script setup>
  import Cabecalho from './components/Header.vue';
  import Balance from './components/Balance.vue';
  import Costs from './components/Costs.vue';
  import History from './components/History.vue';
  import New from './components/New.vue'

  import {ref, computed} from 'vue'

  const itens = ref( [
        {
            text: 'Sneakers',
            value: -200,
            id: Math.floor(Math.random()*10000000)
        },
        {
            text: 'Boats',
            value: 50,
            id: Math.floor(Math.random()*10000000)
        },
        {
            text: 'Rat',
            value: -100,
            id: Math.floor(Math.random()*10000000)
        }
    ]
  )

  const total = computed(() => {
    return itens.value.reduce((acc, plus) => {
      return acc + plus.value
    }, 0)
  })

  // EXPENSE 
  const expense = computed(() => {
    return itens.value.filter((item) => item.value < 0).reduce((acc, plus) => {
      return acc + plus.value
    }, 0).toFixed(2)
  })

  const income = computed(() => {
    return itens.value.filter((item) => item.value > 0).reduce((acc, plus) => {
      return acc + plus.value
    }, 0).toFixed(2)
  })

  const data = (data) =>{
    itens.value.push({
      id: generateUniqueId(),
      text : data.text,
      value : data.amount
    })
  } 

  const generateUniqueId = () => {
    return Math.floor(Math.random() * 100000000)
  }

  const deletar = (id) =>{
    itens.value = itens.value.filter((transaction) => transaction.id !== id)
  }

</script>

<template class="bg-dark-subtle">

  <Cabecalho></Cabecalho>

  <main>
    <Balance :total="+total" />
    <Costs :expense="-expense" :income="+income" />
    <History :transactions="itens" @transaction_delete="deletar"/>
    <New  @newTransaction="data" />
  </main>

</template>

