<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!-- Box 1 -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Cases
      </h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ stats.NewConfirmed }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ stats.TotalConfirmed }}
      </div>
    </div>
    <div class="shadow-md bg-yellow-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">
        Cases
      </h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ stats.NewDeaths }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ stats.TotalDeaths }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "DataBoxes",
  props: {
    stats: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
