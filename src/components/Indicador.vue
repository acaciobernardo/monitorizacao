<template>
  <div class="indicador">
    <p class="titulo">{{ titulo }}</p>
    <div class="corpo">
        <div class="valores">{{ valor }}</div>
        <div class="rodape">{{ rodape }}</div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Indicador',
  props: {
    titulo: String,
    valor: String
  },
  data () {
    return {
      rodape: '======='
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.indicador {
  background: #42b983;
  max-width: 120px;
  min-height: 120px;
  position: relative;
  font-size: small;
  border-radius: 20px;
}

.indicador .titulo {
   margin-top: 0 auto;
   padding-top: 8px;  

   font-size: small;
}

.indicador .corpo {
  padding: 2%;
  width: 100%;
}

.indicador .rodape {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  color: #fff;
  text-align: center;
  font-size: x-small;
}

</style>
