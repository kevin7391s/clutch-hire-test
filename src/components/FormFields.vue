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

<style scoped>
.submit-btn {
  background-color: #0b476c;
  color: #ffffff;
  font-size: 13.45px;
  font-family: "ABeeZee", sans-serif;
  font-weight: 400;
  font-size: 13.45px;
  line-height: 16px;
  letter-spacing: 0%;
  width: 131px;
  height: 34.83px;
  padding: 10.22px 37.5px 8.61px 37.5px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 51.61px;
  margin-left: 179.76px;
  margin-right: 35px;
  display: block;
}
</style>
