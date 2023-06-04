<template>
  <div class="indicadores-container">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
      <Indicador v-for="di in dados" 
      :id="di.id"
      :key="di.titulo"
      :titulo="di.titulo" 
      :valor="di.valor"
      :footer="di.footer"
      />
    
  </div>
</template>

<script>
// @ is an alias to /src
import { ref, onMounted } from 'vue'
import axios from 'axios';
import Indicador from '@/components/Indicador.vue'

export default {
  name: 'HomeView',
  components: {
    Indicador
  },
  props : {
    id: {
    type: Number,
    default: null,
  }
  },
  setup(props) {
    
    const dados = ref([]);

    

    let url = "http://localhost:3000/dados";
   
    if (props.id) {
        url = url + "/id/" + id;
     }
    
    console.log(url);
    
    axios.get(url)
     .then(response => {
        dados.value = response.data;
      })
     .catch(error => {
        console.error(error);
      });


    // onMounted(() => {
    //   axios.get(url)
    //    .then(response => {
    //       dados.value = response.data;
    //     })
    //    .catch(error => {
    //       console.error(error);
    //     });
    // });

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