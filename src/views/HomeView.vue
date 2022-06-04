<template>
  <div class="HomeView">
    <AnimalSwitch @switch-cat-filter="toggleCatFilter()" />
    <AnimalForm @add-animal="addAnimal" />
    <div
      class="stretch"
      v-for="(animal, index) in animalsView"
      :key="animal.name"
    >
      <AnimalList :animal="animal" @delete-animal="removeAnimal(index)" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import AnimalForm from "@/components/AnimalForm/AnimalForm.vue";
import AnimalList from "@/components/AnimalList/AnimalList.vue";
import AnimalSwitch from "@/components/AnimalSwitch/AnimalSwitch.vue";

export type Animal = {
  name: string;
  type: "dog" | "cat";
};

export default defineComponent({
  name: "HomeView",
  components: {
    AnimalForm,
    AnimalList,
    AnimalSwitch,
  },
  data: () => ({
    showCatsOnly: false,
    animals: [] as Animal[],
  }),
  created() {
    this.animals = JSON.parse(localStorage.getItem("animals") || "[]");
  },
  computed: {
    animalsView() {
      if (this.showCatsOnly) {
        return this.catsOnly;
      }

      return this.animals;
    },
    catsOnly() {
      return this.animals.filter(({ type }) => type === "cat");
    },
  },
  methods: {
    toggleCatFilter() {
      this.showCatsOnly = !this.showCatsOnly;
    },
    addAnimal(animal: Animal | null) {
      const newAnimals = [...this.animals];

      if (animal) {
        newAnimals.push(animal);
      }

      this.animals = newAnimals;
    },
    test() {
      console.log("yes");
    },
    removeAnimal(index: number) {
      const newAnimals = [...this.animals];

      newAnimals.splice(index, 1);

      this.animals = newAnimals;
    },
  },
  watch: {
    animals(newAnimals) {
      localStorage.setItem("animals", JSON.stringify(newAnimals));
    },
  },
});
</script>

<style scoped lang="scss">
.HomeView {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
}

.stretch {
  width: 80%;
  margin-right: -15%;
}
</style>
