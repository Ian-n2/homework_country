<template lang="html">
  <div>
    <h1>Countries of the world</h1>
    
    <!-- <select id="country_select" v-model='selectedCountry'>
      <option  v-for="country in countries" :value="country">{{country.name}}</option>
    </select> -->
      <!-- <option disabled value="">Select a country</option> -->
 <country-list  :countries="countries"></country-list>
<country-detail :country="selectedCountry"></country-detail>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import countriesList from './components/countriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country)=>{
      this.selectedCountry = country;
    })
  },
  components: {
    "country-list": countriesList,
    'country-detail': CountryDetail

  }
}
</script>

<style lang="css" scoped>
</style>
