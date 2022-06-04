<template>
  <div class="AnimalForm">
    <input class="" type="text" v-model="animalName" />
    <select class="btn" v-model="animalType">
      <option value="cat">Cat</option>
      <option value="dog">Dog</option>
    </select>
    <button
      class="btn btn-primary"
      @click="$emit('add-animal', this.newAnimal)"
    >
      Add Animal
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { Animal } from "@/views/HomeView.vue";

export default defineComponent({
  name: "AnimalForm",
  data: () => ({
    animalName: "" as string,
    animalType: "cat",
  }),
  computed: {
    newAnimal() {
      if (this.animalName) {
        return {
          name: this.animalName,
          type: this.animalType,
        } as Animal;
      }
      return null;
    },
  },
});
</script>

<style scoped lang="scss">
.AnimalForm {
  display: flex;
  gap: 10px;
}
</style>
