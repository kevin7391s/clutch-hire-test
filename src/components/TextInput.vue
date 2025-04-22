<template>
  <div class="text-input">
    <label :for="name">{{ label }}</label>
    <!-- Input field inherits its id, name, type, and placeholder from props -->
    <input
      :id="name"
      :name="name"
      :type="type"
      :value="modelValue"
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
