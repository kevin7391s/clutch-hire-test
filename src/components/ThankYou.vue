<template>
  <div class="thank-you-container">
    <img src="@/assets/greentech 1.png" alt="GreenTech logo" class="logo" />
    <p class="thank-text">
      Thank you<br />
      <span class="thank-subtext">We will contact you shortly</span>
    </p>
  </div>
</template>

<script lang="ts">
export default {
  name: "ThankYou",
};
</script>

<style scoped>
.thank-you-container {
  width: 227px;
  height: 116px;
  background-color: #f4f2ee;
  position: relative;
  font-family: "Roboto", sans-serif;
}

.logo {
  position: absolute;
  top: 30px;
  left: 35px;
  width: 122.83px;
  height: 40px;
}

.thank-text {
  position: absolute;
  top: 366px;
  left: 83px;
  width: 227px;
  height: 116px;
  font-size: 25px;
  font-weight: 400;
  color: #555552;
  text-align: center;
  line-height: 1;
}

.thank-subtext {
  display: block;
  margin-top: 25px;
}
</style>
