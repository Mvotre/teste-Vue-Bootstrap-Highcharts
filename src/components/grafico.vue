<template>
  <div id="ctn__comp__grafico">
    <h4 class="text-center text-black-50"> Título da área de gráficos </h4>
    <div id="ctn__grafico"></div>
  </div>
</template>

<script>
import axios from 'axios';

import * as grafico from '../assets/js/highcharts.js';
import * as dados from '../assets/js/dadosGrafico.json'; 

export default {
  name: 'grafico',
  data() {
    return {
      dados: dados.default,
      campo0: '',
      campo1: ''
    }
  },
  created(){

    // Trata a resposta do JSON. Se existissem mais de 2 valores, faria um loop ao invés de chamar a função individualmente...
    this.criaCampos(0);
    this.criaCampos(1);
  },

  mounted() {
    const campo1 = this.campo0;
    const campo2 = this.campo1

    document.addEventListener('DOMContentLoaded', function () {
    var myChart = Highcharts.chart('ctn__grafico', {
        chart: {
        type: 'area'
      },
      title: {
          text: 'Gráfico ilustrativo para teste de front-end'
      },
      xAxis: {
          categories: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'],
          tickmarkPlacement: 'on',
          title: {
              enabled: false
          }
      },
      yAxis: {
          title: {
              text: 'Unidades'
          }
      },
      tooltip: {
          split: true,
          valueSuffix: ' unidades'
      },
      plotOptions: {
          area: {
              stacking: 'normal',
              lineColor: '#666666',
              lineWidth: 1,
              marker: {
                  lineWidth: 1,
                  lineColor: '#666666'
              }
          }
      },
      series: [{
          name: 'Campo 1',
          data: campo1
      }, {
          name: 'Campo 2',
          data: campo2
      }]
    });
});
  },

  methods: {
    // Trata a resposta do Json, simulando o tratamento de uma resposta de uma API

    // Pega o json, e cria um novo array só com o campo valor
    criaCampos(num){
      let retorno = this.dados[num].map(elem => elem[1]);
      let nomeVariavel = `campo${num}`

      this[nomeVariavel] = retorno;
    }
  }


}
</script>

<style scoped>

#ctn__comp__grafico {
  margin-top: 20px;
}

#ctn__grafico {
  width: 100%;
  height: 400px;
}

</style>
