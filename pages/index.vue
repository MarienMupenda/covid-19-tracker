<template>
  <div>
    <Header/>
   <DataTitle :title="title" :dataDate="dataDate"/>
    <main v-if="!loading" class="container">
      show data
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
import DataTitle from "../components/DataTitle";
export default {
  name: 'Home',
  components: {DataTitle},
  loading: false,

  data() {
    return {
      title: 'Home',
      loading: true,
      dataDate: '',
      status: {},
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

    this.dataDate = data.Date
    this.countries = data.Countries
    this.status = data.Global
    this.loading = false
  },
  mounted() {
    console.log("mounted")
  }
}
</script>

