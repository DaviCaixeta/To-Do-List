<template>
  <div>
    <h2 class="title-tasks">Tarefas</h2>
    <ul class="to-do-list">
      <li
        v-for="(toDo, index) in listaAfazeres"
        :key="toDo.name"
        class="each-to-do"
      >
        {{ toDo.name }}
        <button
          class="delete-button"
          @click="(toggleModal = true), (posicao = index)"
        >
          X
        </button>
        <ModalConfirm
          v-if="toggleModal"
          @close-modal="toDoRemove(posicao)"
          @cancel-modal="toggleModal = false"
        ></ModalConfirm>
      </li>
    </ul>
  </div>
</template>
<script setup>
import ModalConfirm from "./ModalConfirm.vue";
import { ref, defineProps, defineEmits } from "vue";

defineProps({
  listaAfazeres: Array,
});

const emits = defineEmits(["delete-task"]);

const toggleModal = ref(false);

const toDoRemove = (index) => {
  emits("delete-task", index);
  toggleModal.value = false;
};
</script>

<style scoped>
.title-tasks {
  margin-top: 60px;
  border-bottom: 3px solid black;
  padding-bottom: 20px;
}
.to-do-list {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding-left: 5px;
  margin-top: 30px;
}
.each-to-do {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 3px solid black;
  border-radius: 5px;
  color: white;
  padding: 5px 5px;
  margin-bottom: 20px;
  width: 300px;
  height: auto;
  font-weight: bold;
  background-color: rgb(60, 64, 68);
}
.delete-button {
  background-color: red;
  font-weight: bold;
  margin-left: 10px;
  height: 30px;
  width: 30px;
  align-self: center;
  cursor: pointer;
  border-radius: 4px;
}
.modal-offline {
  display: none;
}
.modal-online {
  display: flex;
  justify-content: center;
  width: 1000px;
}
</style>
