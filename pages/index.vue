<template>
  <div>
    <Header/>
    <main v-if="!loading" class="container">

      <DataTitle :text="title" :dataDate="dataDate"/>
      <DataBoxes :stats="stats"/>
    </main>
    <main v-else class="flex flex-col align-center justify-center text-center">
      <div class="text-gray-500 texy-3xl mt-10 mb-6">
        Fetching data...
      </div>
      <img :src="loadingImage">
    </main>

  </div>
</template>
<script lang="js">
import DataBoxes from "../components/DataBoxes";

export default {
  name: 'Home',
  components: {DataBoxes},
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
    }
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
  },
  mounted() {
    console.log("mounted")
  }
}
</script>

