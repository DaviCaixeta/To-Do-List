<template>
  <div v-bind:class="showModal">
    <div class="modal-content">
      <div class="modal-body">
        <p class="modal-text">Tem certeza que deseja remover essa atividade?</p>
        <button class="buttons-modal" @click="emitModal(true)">
          Confirmar
        </button>
        <button class="buttons-modal" @click="emitModal(false)">
          Cancelar
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, defineProps, defineEmits } from "vue";

const props = defineProps(["modal"]);
const emits = defineEmits(["modal-hidden", "task-remove"]);

const showModal = computed(function () {
  return props.modal === true ? "modal-on" : "modal-off";
});

function emitModal(boolean) {
  if (boolean === true) {
    emits("task-remove");
  } else {
    emits("modal-hidden");
  }
}
</script>

<style scoped>
.modal-on {
  position: fixed;
  display: flex;
  align-items: center;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.4);
}
.modal-off {
  display: none;
}
.modal-content {
  min-width: 370px;
  width: 600px;
  height: 100px;
  background: #fff;
  margin: auto;
  border: 2px solid #000000;
}
.modal-text {
  font-weight: bold;
  color: black;
}
.buttons-modal {
  margin: 10px 55px;
  background-color: lightblue;
  font-weight: bold;
  padding: 5px;
  cursor: pointer;
}
</style>
