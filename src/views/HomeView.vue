<template>
  <div class="home">
    <h1 class="title-page">Lista de Tarefas</h1>
    <InputToDo @is-clicked="buttonClicked" />
    <ShowList :listaAfazeres="lista" @delete-task="deleteTask" />
  </div>
</template>

<script setup>
// @ is an alias to /src
import InputToDo from "@/components/InputToDo.vue";
import ShowList from "@/components/ShowList.vue";
import { reactive } from "vue";

const lista = reactive([]);

function buttonClicked(input) {
  lista.push({ name: input });
}

function deleteTask(index) {
  lista.splice(index, 1);
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
