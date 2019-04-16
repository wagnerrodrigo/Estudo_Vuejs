<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- Exibindo tituto -->
    <h1 v-once v-text="titulo"></h1>
    <h2 v-text="titulo"></h2>

    <h3>{{ subtitulo }}</h3>

    <input :disabled="tarefas.length ==0" v-model="subtitulo" type="text">

    <div v-if="tarefas.lenght <= 0">Não há tarefas</div>

    <div v-if="tarefas.length > 0">
      <br>

      Existem {{tarefas.length}} tarefas.
      <ul>
        <li v-for="tarefa in tarefas">{{tarefa}}</li>
        <p>{{total}}</p>
      </ul>

      <button @click="calcula('-')">-</button>
      <button @click="calcula('+')">+</button>
      <button @click="tarefas = []">Limpar</button>

      <p>Nome inicial: {{nome}} </p>
      <p>Nome filtrado: {{nome | formataNome}} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "lv-tarefas",
  data() {
    return {
      titulo: "lista de tarefa",
      subtitulo: "Defina uma descrição",
      tarefa: ["asdf"],
      tarefas: ["ligar para funlando"],
      total: 10,
      nome: 'wagner rodrigo da silva'
    };
  },
  mounted() {
    setTimeout(() => {
      this.titulo = "Tarefa disponiveis";
      this.tarefas = ["tarefa 1", "tarefa 2", "tarefa 3"];
    }, 1000);
  },
  methods: {
    calcula(sinal) {
      this.total = sinal == "-" ? this.total - 1 : this.total + 1;
    }
  },
  filters:{
    formataNome(valor){
      console.log('Executando filter')
      valor = valor.toLowerCase()
      let corta = valor.split(' ')
      let resultado = ''
      for(let nome of corta)
      resultado += nome.charAt(0).toUpperCase() + nome.slice(1) + ' ' 
      return resultado
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
