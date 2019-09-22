<template>
  <div id="ctn__comp__tabela">
    <h4 class="text-center text-black-50"> Título da área de tabela </h4>

    <div class="table-responsive">
      <table class="table table-striped table-hover">

        <thead class="thead-light">
          <th> ID </th>
          <th> Nome </th>
          <th> Telefone </th>
          <th> E-mail </th>
          <th> Site </th>
        </thead>

        <tbody>
          <tr v-for="(item,index) in infoTabela" :key="index">
            <td> {{item.id}} </td>
            <td> {{item.name}} </td>
            <td> {{item.phone}} </td>
            <td> {{item.email}} </td>
            <td> {{item.website}} </td>
          </tr>
        </tbody>
        
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'tabela',
  data() {
    return {
      infoTabela: ''
    }
  },
  created(){
    // Chama o método para popular a tabela
    this.buscaDados();
  },
  methods: {
    // Busca os dados da tabela
     buscaDados(){
      axios.get('https://jsonplaceholder.typicode.com/users')
      // Sucesso
      .then((response) => {
        this.infoTabela = response.data
      })
      // Tratamento de erro
      .catch((error) => {
        console.log(error);
      });  
    },
  }
}
</script>

<style scoped>
#ctn__comp__tabela {
  margin: 30px 0;
}

#ctn__comp__tabela h4 {
  margin-bottom: 20px;
}

</style>
