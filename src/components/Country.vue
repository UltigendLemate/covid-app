<template>
   <select v-model="selected" @change="onChange()" class="form-select mb-10 mt-10 block w-full border p-3 rounded ">
   <option value="0">Select Country</option>
   <option v-for="(country,i) in countries" :key="i" :value="country.ID">
      {{ country.Country }}
    </option>
   </select >
</template>

<script>
export default {
    name:'Country',
    props : ['countries'],
    data(){
        return{
            selected:0,
        }
    },
    methods:{

        onChange(){
            const country = this.countries.find((item)=>item.ID===this.selected)
        console.log(country)
        this.$emit('get-country',country) 
        }  
    }
}
</script>