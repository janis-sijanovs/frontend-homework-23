<template>
  <div class="switch">
    <div class="form-check form-switch">
      <label class="form-check-label" for="flexSwitchCheckDefault"
        >Show Cats Only</label
      >
      <input
        @input="$emit('switch-cat-filter')"
        class="form-check-input"
        type="checkbox"
        role="switch"
        id="flexSwitchCheckDefault"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "AnimalSwitch",
});
</script>

<style scoped lang="scss">
.switch {
  width: fit-content;
  align-self: flex-end;
}
</style>
