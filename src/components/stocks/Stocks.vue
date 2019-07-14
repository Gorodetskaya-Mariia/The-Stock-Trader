<template>
  <div class="container-stocks">
    <app-stock v-for="stock in stocks" :key="stock"></app-stock>
  </div>
</template>

<script>
  import Stock from "./Stock.vue";
  export default {
    data() {
      return {
        stocks: [
          { id: 1, name: "BMW", price: 100 },
          { id: 2, name: "Google", price: 200 },
          { id: 3, name: "Apple", price: 300 },
          { id: 4, name: "Twitter", price: 400 }
        ]
      }
    },
    components: {
      appStock: Stock
    }
  }
</script>

<style scope>
  .container-stocks {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
</style>
