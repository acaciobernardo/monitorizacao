<template>
  <div class="indicador">
    <p class="titulo">{{ titulo }}</p>
    <div class="corpo">
        <div class="valor">
          <div style="width: 30px;">&nbsp;</div>
          <div :cor="getColor(valor)"> {{ valor }}%</div>
          <div style="width: 30px;">&nbsp;</div>
        </div>
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
  color: antiquewhite;
  background-color: rgba(75, 98, 97, 0.896);
  max-width: 150px;
  min-width: 150px;
  min-height: 150px;
  position: relative;
  font-size: small;
  border-radius: 20px;
}

[cor="red"] {
  background: #f44336; /* red */
}

[cor="orange"] {
  background: #ff9800; /* orange */
}

[cor="green"] {
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

.indicador .corpo div.valor {
  display: flex;
  justify-content: space-evenly;
}

.indicador .corpo div.valor div{
  height: 45px;
  width: 45px;
}

.indicador .corpo div.valor div:nth-child(2) {
  /* background-color: antiquewhite; */
  color: white;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
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
