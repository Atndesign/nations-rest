<template>
  <div id="detail">
    <Header />
    <div class="top-controls">
      <BackBtn @close-detail="closeDetailView" />
    </div>

    <div class="infos" v-if="countryInfos?.flag">
      <img
        class="details__flag"
        v-if="countryInfos?.flag"
        :src="countryInfos.flag"
      />
      <div class="infos__main">
        <p class="content__country-name">{{ countryInfos.name }}</p>
        <div class="main__infos">
          <div class="infos__content">
            <p class="content__name">
              Native name:
              <span class="content__value">
                {{ countryInfos.nativeName }}
              </span>
            </p>
            <p class="content__name">
              Population:
              <span class="content__value">
                {{
                  countryInfos.population
                    .toString()
                    .replace(/(\d)(?=(\d\d\d)+(?!\d))/g, "$1,")
                }}
              </span>
            </p>
            <p class="content__name">
              Region:
              <span class="content__value">
                {{ countryInfos.region }}
              </span>
            </p>
            <p class="content__name">
              Sub region:
              <span class="content__value">
                {{ countryInfos.subregion }}
              </span>
            </p>
            <p class="content__name">
              Capital:
              <span class="content__value">
                {{ countryInfos.capital }}
              </span>
            </p>
          </div>
          <div class="infos__content">
            <p class="content__name">
              Top level domain:
              <span class="content__value">
                {{
                  countryInfos.topLevelDomain
                    .map((domain) => {
                      return domain;
                    })
                    .toString()
                }}
              </span>
            </p>
            <p class="content__name">
              Currencies:
              <span class="content__value">
                {{
                  countryInfos.currencies
                    .map((currency) => currency.name + " ")
                    .toString()
                }}
              </span>
            </p>
            <p class="content__name" v-if="countryInfos?.languages">
              Languages:
              <span class="content__value">
                {{
                  countryInfos.languages
                    .map((language) => language.name + " ")
                    .toString()
                }}
              </span>
            </p>
          </div>
        </div>
        <div class="content__borders">
          <p class="borders__title" v-if="countryInfos?.languages">
            Border countries:
          </p>
          <div class="borders__items">
            <button
              class="borders__item"
              v-for="(border, index) in countryInfos.borders"
              :key="index"
              @click="fecthCountry(border)"
            >
              {{ border }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "../header";
import BackBtn from "../back";
import axios from "axios";

export default {
  name: "Details",
  components: {
    Header,
    BackBtn,
  },
  props: {
    country: String,
  },
  data() {
    return {
      countryInfos: {},
    };
  },
  mounted() {
    axios
      .get(`https://restcountries.eu/rest/v2/name/${this.country}`)
      .then((data) => {
        this.countryInfos = data.data[0];
      });
  },

  methods: {
    closeDetailView() {
      this.$emit("close-detail");
    },
    fecthCountry(countryCode) {
      console.log(countryCode);
      axios
        .get(`https://restcountries.eu/rest/v2/alpha/${countryCode}`)
        .then((data) => {
          this.countryInfos = data.data;
        });
    },
  },
};
</script>

<style></style>
