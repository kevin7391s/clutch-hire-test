<template>
  <form @submit.prevent="onSubmit" class="form-fields">
    <!-- Each TextInput receives a label, name, and two-way v-model binding -->
    <TextInput label="First Name" name="first" v-model="first" />
    <TextInput label="Last Name" name="last" v-model="last" />
    <TextInput label="Email" name="email" type="email" v-model="email" />
    <TextInput label="Phone Number" name="phone" v-model="phone" />
    <TextInput label="Company" name="company" v-model="company" />

    <!-- Submit button emits a 'submit' event to the parent component -->
    <button type="submit" class="submit-btn">Continue</button>
  </form>
</template>

<script lang="ts">
import { defineComponent, toRefs } from "vue";
import TextInput from "./TextInput.vue";

export default defineComponent({
  name: "FormFields",
  components: { TextInput },
  // Accepts 'form' object from parent component (e.g. FormView.vue)
  props: {
    form: {
      type: Object,
      required: true,
    },
  },
  emits: ["submit"],
  setup(props, { emit }) {
    // Converts props.form into individual reactive refs to stay connected to parent
    const { first, last, email, phone, company } = toRefs(props.form);

    const onSubmit = () => {
      emit("submit");
    };

    return {
      first,
      last,
      email,
      phone,
      company,
      onSubmit,
    };
  },
});
</script>
