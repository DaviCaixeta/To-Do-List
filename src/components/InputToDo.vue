<template>
  <div>
    <div class="container-input">
      <input
        placeholder="O que necessitas fazer?"
        type="text"
        name="inputToDo"
        v-model="input"
        class="input-task"
      />
      <button type="submit" @click="buttonClicked()" class="button-submit">
        +
      </button>
    </div>
  </div>
</template>
<script setup>
import { ref, defineEmits } from "vue";

const emits = defineEmits(["is-clicked"]);

var input = ref("");

function buttonClicked() {
  if (input.value !== "") {
    emits("is-clicked", input.value);
    input.value = "";
  }
}
</script>

<style scoped>
.container-input {
  display: flex;
  justify-content: flex-start;
}
.input-task {
  height: 30px;
  border-radius: 5px;
  border: 3px solid black;
  width: 300px;
  font-weight: bold;
  color: black;
  margin-left: 5px;
}
.button-submit {
  background-color: lightblue;
  margin-left: 15px;
  cursor: pointer;
  height: 35px;
  width: 35px;
  border-radius: 20px;
  color: green;
  font-weight: bold;
  font-size: 20px;
}
</style>
