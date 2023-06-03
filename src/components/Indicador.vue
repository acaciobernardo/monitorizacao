<template>
  <div class="indicador" :cor="getColor(valor)">
    <p class="titulo">{{ titulo }}</p>
    <div class="corpo">
        <div class="valores">{{ valor }}%</div>
        <div class="rodape">
            <div><hr/></div>
            <div>
              {{ (footer) ? footer : '&nbsp;' }}
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Indicador',
  props: {
    titulo: String,
    valor: Number,
    footer: String
  },
  data () {

    const getColor = (val) => {
      if (val<50) {
        return 'red';
      } else if (val>=70) {
        return 'green'; 
      } 
      else {
        return 'orange';
      }
    }

    return {
      getColor
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.indicador {
  max-width: 120px;
  min-width: 120px;
  min-height: 120px;
  position: relative;
  font-size: small;
  border-radius: 20px;
}

.indicador[cor="red"] {
  background: #f44336; /* red */
}

.indicador[cor="orange"] {
  background: #ff9800; /* orange */
}

.indicador[cor="green"] {
  background: #42b983; /* green */
}

.indicador .titulo {
   margin-top: 0 auto;
   padding-top: 8px;  
   font-weight: bold;
   font-size: small;
}

.indicador .corpo {
  padding: 2%;
  width: 100%;
}

.indicador .rodape {
  position: absolute;
  bottom: 3px;
  left: 0;
  width: 100%;
  color: #fff;
  text-align: center;
  font-size: x-small;
}

</style>
