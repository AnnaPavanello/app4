<script setup>
const novaTarefa = ref('')
const aviso = ref(false);
import {ref} from 'vue'
const tarefas = ref ([
  'Prova Matemática',
  'Prova Geografia',
  'Trabalho Sociologia',
  'Seminário Português',
  'Seminário Educação Física',
  'Seminário Geografia',
  'Prova Física'
])
function adicionar (){
  if (novaTarefa.value.length < 5){
    aviso.value = true;
  }
  else {
  tarefas.value.push(novaTarefa.value)
  novaTarefa.value = '';
  }

}
</script>

<template>
  <div class="container">
    <h1>Lista de Tarefas</h1>
    <label>Nova tarefa: <br><input v-model="novaTarefa"type="text" @keyup.enter="adicionarTarefa" @input="aviso = false"></label>
    <button @click="adicionar">add</button>
    <div v-show="aviso" class="aviso">Insira ao menos 5 caracteres!</div>
    <ul>
      <li v-for="tarefa in tarefas" :key="tarefa">
        {{ tarefa }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
</style>
