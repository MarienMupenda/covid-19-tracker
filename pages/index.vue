<template>
  <div>
    <Header/>
    <main v-if="!loading" class="container">
      <CountrySelect :countries="countries" :selected="0"/>
      <DataTitle :text="title" :dataDate="dataDate"/>
      <DataBoxes :stats="stats"/>
      <CountrySelect :countries="countries" :selected="selectedCountry" />
      <button class="btn btn-primary btn-lg btn-block">
        <i class="fa fa-user"></i>
        Reset
      </button>
    </main>
    <main v-else class="flex flex-col align-center justify-center text-center">
      <div class="text-gray-500 texy-3xl mt-10 mb-6">
        Fetching data...
      </div>
      <img :src="loadingImage" alt="loading">
    </main>

  </div>
</template>
<script lang="js">

export default {
  name: 'Home',
  loading: false,

  data() {
    return {
      title: 'Global',
      loading: true,
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif'),

    }
  },

  methods: {
    async fetchCovidData() {
      const response = await fetch('https://api.covid19api.com/summary')
      return response.json();
    },
    setCountryData(country) {
      console.log("country set to: " + country.Country);
      this.title = country.Country
      this.stats = country
    },
  },
  async created() {
    console.log("Created")
    const data = await this.fetchCovidData()

    //log  data
    console.log(data)

    this.dataDate = data.Date
    this.countries = data.Countries
    this.stats = data.Global
    this.loading = false

    this.$nuxt.$on('country-selected', (country) => {
      this.setCountryData(country)
      console.log("country selected: " + country.Country)
    })
  },
  mounted() {
    console.log("mounted")
  }
}
</script>

