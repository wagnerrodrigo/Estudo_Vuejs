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
        <li v-for="tarefa in tarefas"> {{tarefa}}</li>
      </ul>

      <button @click="tarefas = []">Limpar</button>
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
      tarefas: ["ligar para funlando"]
    };
  },
  mounted() {
    setTimeout(() => {
      this.titulo = "Tarefa disponiveis";
      this.tarefas = ['tardsf','asdfasdf','asdfasdf'];
    }, 2000);
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
