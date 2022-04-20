<template>
  <div>
    <Header />
    <main v-if="!loading">
      show data
    </main>
    <main v-else>
      loading...
    </main>

  </div>
</template>
<script lang="js">
export default {
  name: 'Home',
  components: {},
  loading: false,

  data(){
    return {
      title: 'Home',
      loading: true,
      dataDate : '',
      status:{ },
      countries: [],
      loadingImage: require('../assets/hourglass.gif'),

    }
  },

  methods :{
    async fetchCovidData(){
      const response = await axios.get('https://api.covid19api.com/summary')
      console.log(response.data)
    }
  },
  async created(){
  const data = await this.fetchCovidData()
  this.dataDate = data.Date
  this.countries = data.Countries
  this.status = data.Global
  this.loading = false
  }
}
</script>

