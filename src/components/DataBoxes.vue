<template>
  <div class="grid gap-4 md:grid-cols-2">


  <!-- Box-1 -->
    <div class="shadow-md bg-blue-100 text-center rounded p-6">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New: </span>
        {{ Comma(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl ">
        <span class="font-bold">Total: </span>
        {{ Comma(stats.TotalConfirmed) }}
      </div>
    </div>


    <!-- Box-2 -->
    <div class="shadow-md bg-blue-200 text-center rounded p-6">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">New: </span>
        {{ Comma(stats.NewDeaths) }}
      </div>
      <div class="text-2xl ">
        <span class="font-bold">Total: </span>
        {{ Comma(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods:{
      Comma(x){
          return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
      }
  }
};
</script>