<script setup>
import { ref } from 'vue';

// variável com tarefas
const tarefas = ref([
  "Estudar JavaScript", 
  "Estudar vue.js",
  "Estudar pra faculdade",
  "Treinar"
])

// criar a função para remover tarefa
function removerTarefa(i) {
  tarefas.value.splice(i, 1)
}

// variável pra nova tarefa
const novaTarefa = ref("");

// função de adicionar
// trim pra tirar excesso de espaços que podem usar
function adicionarTarefa() {
  if(novaTarefa.value.trim() !== "") {
    tarefas.value.push(novaTarefa.value.trim())
    novaTarefa.value = ""
  }
}
</script>

<template>
<h1>📝 Lista de Tarefas</h1>
<!-- fazendo um parágrafo condicional -->
<div v-if="tarefas.length === 0">
  <p>Parabéns!! Você é top! Master! Blaster!</p>
</div>
<!-- adicionando o else por boas práticas -->
<ul v-else>
  <!-- fazendo o v-for, passando os parâmetros e dizendo de qual lugar pegar os dados -->
   <!-- :key sendo como um id para identificar cada item -->
  <li v-for="(tarefa, index) in tarefas" :key="index" >{{ tarefa }} <button @click="removerTarefa(index)">❌ Remover</button></li>
</ul>

<section>
  <input type="text" placeholder="Digite sua nova tarefa" v-model="novaTarefa">
  <button @click="adicionarTarefa">Adicionar</button>
</section>
</template>