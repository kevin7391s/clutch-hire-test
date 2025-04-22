<template>
  <div class="form-container">
    <!-- Logo displayed above the form, matching the Figma design -->
    <img src="@/assets/greentech 1.png" alt="GreenTech logo" class="logo" />

    <!-- FormFields handles all input UI. Passes down form object by v-model and listens for submit -->
    <FormFields v-model:form="form" @submit="onSubmit" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";
import FormFields from "@/components/FormFields.vue";

export default defineComponent({
  name: "FormView",
  components: {
    FormFields,
  },
  setup() {
    // Create a reactive form object containing all the user input fields
    const form = reactive({
      first: "",
      last: "",
      email: "",
      phone: "",
      company: "",
    });

    const onSubmit = () => {
      console.log("Form submitted:", form);
    };

    return {
      form,
      onSubmit,
    };
  },
});
</script>
