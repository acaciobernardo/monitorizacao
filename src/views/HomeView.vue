<template>
  <div>{{ idPai }}</div>
  <div class="indicadores-container">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->

   

     <Indicador 
     v-for="di in dados" key="di.id"  
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
import { ref } from "vue";
import axios from 'axios';
import Indicador from '@/components/Indicador.vue'

export default {
  name: 'HomeView',
  components: {
    Indicador
  },
  props : {
    id: {
    type: String,
    default: null
  }},
  data() {
    
    const dados = ref([]);
    const idPai = null;
    
    return { dados, idPai }
  },  
  updated() {
     console.log("update " + this.id+ " pai:"+this.idPai);
     let url = "http://localhost:3000/dados";
     if (this.id) {
      url = url + "/" + this.id
     }

     if (this.id !== this.idPai) {
      
      this.idPai = this.id;

      axios.get(url)
        .then(response => {
          console.log(response.data);
          if (this.id) {
            this.dados = [response.data];
          } else {
            this.dados = response.data;
          }
        })
        .catch(error => {
          console.error(error);
        });
    

     }

  

    },
    mounted() {
      console.log("mounted");
      this.dados = [];
      let url = "http://localhost:3000/dados/";
    
      this.dados = [];

      axios.get(url)
        .then(response => {
          console.log(response.data);
          this.dados = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    

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