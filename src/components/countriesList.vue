<template lang="html">
  <div>
    <label for="country_select">Select a country</label>
    <select id="country_select" v-on:change="handleClick" v-model='selectedCountry'>
      <option  v-for="(country, index) in countries" :value="country" :key="index">{{country.name}}</option>
    </select>
    <!-- <ul>
      <list-item v-for="(country, index) in countries" :country="country" :key="index">
</list-item>
    </ul> -->
  </div>
</template>

<script>

import{ eventBus} from '../main.js'
export default {
  name: 'country-list',
  data(){
    return{
    selectedCountry: []
  }
  },
  props: ['countries'],
  components: {
    // "list-item": ListItem
  },
  methods: {
    handleClick(){
      eventBus.$emit("country-selected", this.selectedCountry)
}
}
}
</script>

<style lang="css" scoped>
</style>
