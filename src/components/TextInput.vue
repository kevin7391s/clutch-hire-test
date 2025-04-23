<template>
  <div class="input-wrapper">
    <!-- Input field inherits its id, name, type, and placeholder from props -->
    <label class="floating-label" :for="name">{{ label }}</label>
    <input
      :id="name"
      :name="name"
      :type="type"
      :value="modelValue"
      class="styled-input"
      @input="
        // Emits the user value as user types, targeted as HTMLInputElement
        $emit('update:modelValue', ($event.target as HTMLInputElement).value)
      "
    />
  </div>
</template>

<script lang="ts">
export default {
  name: "TextInput",
  // Props define input behavior and allow parent components to control content
  props: {
    label: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      default: "text",
    },
    modelValue: {
      type: String,
      default: "",
    },
  },
  emits: ["update:modelValue"],
};
</script>

<style scoped>
.input-wrapper {
  position: relative;
  width: 310px;
  margin-bottom: 31.91px;
}

.floating-label {
  position: absolute;
  top: -6px;
  left: 12px;
  font-size: 12px;
  font-family: "ABeeZee", sans-serif;
  color: #5a9a63;
  background-color: #f4f2ee;
  padding: 0 4px;
  pointer-events: none;
  z-index: 1;
}

.styled-input {
  font-family: "ABeeZee", sans-serif;
  font-size: 15px;
  font-weight: 400;
  color: #555552;
  line-height: 1;

  width: 100%;
  height: 40.32px;
  padding: 10px 12px 4px 16px;
  border: 0.72px solid #555555;
  border-radius: 3.6px;
  background-color: transparent;
  box-sizing: border-box;
}
</style>
