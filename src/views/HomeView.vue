<template>
  <main-layout>
    <div>{{ idPai }}</div>
    <div class="indicadores-container">
      <Indicador v-for="di in dados" key="di.id" :id="di.id" :key="di.titulo" :titulo="di.titulo" :valor="di.valor"
        :footer="di.footer" />
    </div>
  </main-layout>
</template>

<script>
// @ is an alias to /src
import { ref } from "vue";
import axios from 'axios';
import Indicador from '@/components/Indicador.vue'
import MainLayout from '@/components/MainLayout.vue'

async function getData(urlBase) {
  try {
    const response = await axios.get(urlBase);
    return response.data;
  } catch (error) {
    console.error(error);
    return null;
  }
}


export default {
  name: 'HomeView',
  components: {
    Indicador,
    MainLayout
  },
  props: {
    id: {
      type: String,
      default: null
    }
  },
  data() {

    const dados = ref([]);
    const idPai = null;
    const urlBase = "http://localhost:3000/dados";

    return { dados, idPai, urlBase }
  },
  updated() {
    //console.log("update " + this.id + " pai:" + this.idPai);

    if (this.id !== this.idPai) {

      this.idPai = this.id;

      let url = this.urlBase;
      if (this.id) {
        url = url + "/" + this.id
      }

      getData(url).then((data) => {
        if (this.id) {
          this.dados = [data];
        } else {
          this.dados = data;
        }
      })

    }

  },
  mounted() {
    // console.log("mounted");
    this.dados = [];

    getData(this.urlBase).then((data) => {
      this.dados = data;
    })

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
  margin: 10px 10px 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
</style>