<template lang="html">
  <div v-if='country'>
    <h3>{{country.name}}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <img :src='country.flag' alt="flag">
    <p>languages</p>
    <ul>
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    </div>
</template>

<script>
export default {
  name: 'country-detail',
  props:['country']
}
</script>

<style lang="css" scoped>
</style>
