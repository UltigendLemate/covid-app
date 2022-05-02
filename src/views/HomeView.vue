<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate"/>
    <DataBoxes :stats="stats"/>
    <Country @get-country="getCountryData" :countries="countries"/>
<div class="flex w-full justify-center">
    <button @click="clearCountryData" v-if="stats.Country" class="text-white  p-5 w-3/5 mb-10 mx-auto bg-green-800 rounded-md">Clear Country</button></div>
  </main>
  <main class="flex flex-col justify-center align-center text-center " v-else>
  <div class="mt-10 text-3xl text-gray-500 mb-6" >Fetching Data</div>
  <img :src="loadingImage" alt="loading" class="w-24 m-auto">
  </main>
</template>


<script>
// @ is an alias to /src
import DataBoxes from '../components/DataBoxes.vue'
import DataTitle from '../components/DataTitle.vue'
import Country from '../components/Country.vue'
export default {
  name: 'HomeView',
  data(){
    return{
    loading:true,
    title:'Global',
    countries:[],
    dataDate :'',
    stats:{},
    loadingImage: require('../assets/hourglass.gif')}
  },
  components: {
      DataTitle,
      DataBoxes,
      Country
  },
  methods:{
    async clearCountryData(){
      this.loading = true
      this.title = "Global"
const data1 = await this.fetchData()
    this.dataDate = data1.Date
    this.stats = data1.Global
    this.countries = data1.Countries
    this.loading = false
    },
    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },
      async fetchData(){
        const res = await fetch('https://api.covid19api.com/summary')
        const data = await res.json()
        return data
      }
      
  },
  async created(){
    const data1 = await this.fetchData()
    this.dataDate = data1.Date
    this.stats = data1.Global
    this.countries = data1.Countries
    this.loading = false
    // console.log(data1.Countries)
      }
}
</script>
