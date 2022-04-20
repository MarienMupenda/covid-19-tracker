<template>
  <select v-model="selected" class="form-select block w-full border p-3 mt-3 mb-3 rounded" @change="onChange">
    <option value="0">Select Country</option>
    <option v-for="country in countries" :value="country.ID">{{ country.Country }}</option>
  </select>
</template>
Select Country
<script lang="js">
export default {
  name: "CountrySelect",
  props: {
    countries: {
      type: Array,
      required: true
    },
    selected: {
      type: String,
      required: false,
      default: "0"
    }
  },
  methods: {
    onChange: function (event) {
      const country = this.countries.find(
        country => country.ID === this.selected
      );
      this.selected = country.ID;
      console.log("country changed to: " + country.Country);
      $nuxt.$emit("country-selected", country);
    }
  }
}
</script>

<style scoped>

</style>
