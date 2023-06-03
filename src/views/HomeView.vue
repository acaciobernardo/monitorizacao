<template>
  <div class="indicadores-container">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <Indicador v-for="di in dados" :key="di.titulo"
         :titulo="di.titulo" 
         :valor="di.valor"
         :footer="di.footer"  />
    
  </div>
</template>

<script>
// @ is an alias to /src
import Indicador from '@/components/Indicador.vue'
import { ref }  from 'vue'

export default {
  name: 'HomeView',
  components: {
    Indicador
  },
  setup() {
    const dados = ref([{
      id: 1,
      titulo: 'Sites',
      valor: 70,
      footer: 'online há 5 dias'
    },{
      id: 2,
      titulo: 'TRON',
      valor: 90,
      footer: 'online há 5 dias'
    },{
      id: 3,
      titulo: 'Santander',
      valor: 50,
      footer: 'online há 5 dias'
    },{
      id: 4,
      titulo: 'IMTT',
      valor: 10,
      footer: 'online há 5 dias'
    },{
      titulo: 'Webservices MAPFRE',
      valor: 70,
      footer: 'online há 5 dias'
    }
  ])

    return { dados }
  }
}
</script>


<style scoped>

  .indicadores-container {
    display: flex;
    flex: 1;
    flex-wrap: wrap;
  }

  .indicador {
    flex-basis: 150px;
    margin: 10px 10px 20px ;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  }

  

</style>