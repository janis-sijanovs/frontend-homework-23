<template>
  <div class="AnimalList">
    <p>{{ animal?.type }}</p>
    <p>{{ animal?.name }}</p>
    <button class="close-button" @click="$emit('delete-animal')">X</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AnimalList",
  props: {
    animal: Object,
  },
});
</script>

<style scoped lang="scss">
.AnimalList {
  width: 80%;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  background-color: salmon;
  border-radius: 20px;
  border: 2px solid black;
}

.AnimalList p {
  margin: 0;
  font-size: larger;
  font-weight: bold;
  color: rgb(36, 0, 3);
}

.close-button {
  cursor: pointer;
  border: none;
  background-color: transparent;
  color: red;
  font-size: larger;
  font-weight: bolder;

  &:hover {
    color: rgb(156, 0, 0);
  }

  &:active {
    color: rgb(114, 0, 0);
  }
}
</style>
