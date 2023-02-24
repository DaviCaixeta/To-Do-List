<template>
  <div class="home">
    <button @click="teste()">zzzz</button>
    <h1 class="title-page">Lista de Tarefas</h1>
    <InputToDo v-model:inputTask="input" @is-clicked="buttonClicked" />
    <ShowList :listaAfazeres="lista" @delete-task="deleteTask" />
  </div>
</template>

<script setup>
// @ is an alias to /src
import InputToDo from "@/components/InputToDo.vue";
import ShowList from "@/components/ShowList.vue";
import { reactive, ref } from "vue";

const lista = reactive([]);
const input = ref("");

function buttonClicked() {
  lista.push({ name: input.value });
  input.value = "";
}

function deleteTask(index) {
  lista.splice(index, 1);
}

function teste() {
  console.log(lista);
}
</script>

<style scoped>
.title-page {
  margin-bottom: 50px;
  display: flex;
  color: mediumblue;
  width: 300px;
  opacity: 0.6;
  padding-top: 20px;
}
.home {
  height: 100vh;
  background-color: lightgrey;
}
</style>
