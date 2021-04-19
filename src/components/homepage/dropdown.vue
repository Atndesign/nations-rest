<template>
  <div class="dropdown">
    <div class="dropdown__select" @click="openDropDown">
      Filter by region
    </div>
    <ul
      class="dropdown__list"
      :style="{ display: isOpen === true ? 'block' : 'none' }"
    >
      <li class="list__item">Africa</li>
      <li class="list__item">America</li>
      <li class="list__item">Asia</li>
      <li class="list__item">Europe</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "DropDown",
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    openDropDown() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style></style>
