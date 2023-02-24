<template>
  <div class="modal-on" @click.prevent.self="$emit('cancel-modal')">
    <div class="modal-content">
      <div class="modal-body">
        <p class="modal-text">Tem certeza que deseja remover essa atividade?</p>
        <button class="buttons-modal" @click="$emit('close-modal')">
          Confirmar
        </button>
        <button class="buttons-modal" @click="$emit('cancel-modal')">
          Cancelar
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";

defineEmits(["close-modal", "cancel-modal"]);
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
