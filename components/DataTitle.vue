<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">{{ title }}</h2>
    <div class="text-2xl mt-4 mb-10"> {{ dataDate }}</div>
  </div>
</template>

<script lang="ts">
import momemt from 'moment';
export default {
  name: "DataTitle",
  props: {
    title: {
      type: String,
      default: "DataTitle"
    },
    dataDate: {
      type: String,
      default: "DataDate"
    }
  },
  computed: {
    dataDate: function() {
      return moment(this.dataDate).format("MMMM Do YYYY");
    }
  }
}
</script>

<style scoped>

</style>
