<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">{{ text }}</h2>
    <div class="text-2xl mt-4 mb-10"> {{ timestamp }}</div>
  </div>
</template>

<script lang="js">
import moment from 'moment';

export default {
  name: "DataTitle",
  props: {
    text: {
      type: String,
      default: "DataText"
    },
    dataDate: {
      type: String,
      default: "DataDate"
    }
  },
  computed: {
    timestamp: function () {

      return moment(this.dataDate).format("MMMM Do YYYY, h:mm:ss a UTC+2")
    },
  }
}
</script>

<style scoped>

</style>
