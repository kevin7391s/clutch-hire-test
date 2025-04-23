<template>
  <div class="form-container">
    <!-- Logo displayed above the form, matching the Figma design -->
    <img src="@/assets/greentech 1.png" alt="GreenTech logo" class="logo" />

    <div v-if="!submitted" class="form-body">
      <h1 class="form-title">Have us reach out</h1>
      <!-- FormFields handles all input UI. Passes down form object by v-model and listens for submit -->
      <FormFields v-model:form="form" @submit="onSubmit" />
    </div>
    <ThankYou v-else />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from "vue";
import FormFields from "@/components/FormFields.vue";
import ThankYou from "@/components/ThankYou.vue";

export default defineComponent({
  name: "FormView",
  components: {
    FormFields,
    ThankYou,
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

    const submitted = ref(false);
    const onSubmit = () => {
      submitted.value = true;

      // Reset form after 5 seconds
      setTimeout(() => {
        submitted.value = false;
        form.first = "";
        form.last = "";
        form.email = "";
        form.phone = "";
        form.company = "";
      }, 5000);
    };

    return {
      form,
      submitted,
      onSubmit,
    };
  },
});
</script>

<style scoped>
.form-container {
  width: 393px;
  height: 852px;
  margin: 0 auto;
  background-color: #f4f2ee;
  font-family: "Roboto", sans-serif;
  box-sizing: border-box;
  position: relative;
  padding: 0;
}

.logo {
  position: absolute;
  width: 122.83px;
  height: 40px;
  top: 30px;
  left: 35px;
}

.form-body {
  position: absolute;
  top: 208px;
  left: 36px;
  right: 36px;
}

.form-title {
  font-size: 25px;
  font-weight: 400;
  color: #555552;
  margin-bottom: 25px;
  line-height: 1;
}
</style>
