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
    const onSubmit = async () => {
      try {
        // Clean phone number of any non digit
        const cleanForm = {
          ...form,
          phone: form.phone.replace(/\D/g, ""),
        };

        console.log(
          "Submitting this data:",
          JSON.stringify(cleanForm, null, 2)
        );

        const response = await fetch(
          `https://dev-api-api.hiring-test.experientialpreview.com/api/lead/${process.env.VUE_APP_API_KEY}`,
          {
            method: "POST",
            headers: {
              "Content-Type": "application/json",
            },
            body: JSON.stringify(cleanForm),
          }
        );

        const responseData = await response.json();
        console.log("API response:", responseData);

        if (!response.ok) {
          console.error("Validation errors:", responseData.errors);
          throw new Error(
            `API returned ${response.status}: ${
              responseData.message || "Unknown error"
            }\nDetails: ${JSON.stringify(responseData.errors, null, 2)}`
          );
        }

        submitted.value = true;

        // Reset the form after 5 seconds
        setTimeout(() => {
          submitted.value = false;
          form.first = "";
          form.last = "";
          form.email = "";
          form.phone = "";
          form.company = "";
        }, 5000);
      } catch (error) {
        console.error("Submission failed:", error);
      }
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
