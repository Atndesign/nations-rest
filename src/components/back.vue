<template>
  <button class="top-controls__back-btn" @click="$emit('close-detail', null)">
    <img class="back-btn__icon" src="../assets/img/back.svg" alt="" />Back
  </button>
</template>

<script>
export default {
  name: "BackBtn",
};
</script>

<style></style>
