<template>
  <div class="indicadores-container">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <Indicador titulo="Webapps internas" valor="12%"  />
    <Indicador titulo="Webapps externas" valor="12%"  />
    <Indicador titulo="Webservices" valor="52%"  />
  </div>
</template>

<script>
// @ is an alias to /src
import Indicador from '@/components/Indicador.vue'

export default {
  name: 'HomeView',
  components: {
    Indicador
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