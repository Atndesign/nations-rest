<template>
  <div class="country-card">
    <div
      class="country-card__cover"
      :style="{ backgroundImage: 'url(' + country.flag + ')' }"
    ></div>
    <div class="country-card__content">
      <p class="country-card__name">{{ country.name }}</p>

      <div class="country-card__infos">
        <p class="infos__name">
          Population:
          <span class="infos__value">
            {{
              country.population
                .toString()
                .replace(/(\d)(?=(\d\d\d)+(?!\d))/g, "$1,")
            }}
          </span>
        </p>
        <p class="infos__name">
          Region:
          <span class="infos__value">
            {{ country.region }}
          </span>
        </p>
        <p class="infos__name">
          Capital:
          <span class="infos__value">
            {{ country.capital }}
          </span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CountryCard",
  props: {
    country: Object,
  },
};
</script>

<style></style>
