<template>
  <div class="container-stocks">
    <app-stock v-for="stock in stocks" :key="stock" :stock="stock"></app-stock>
  </div>
</template>

<script>
  import Stock from "./Stock.vue";
  export default {
    components: {
      appStock: Stock
    },
    computed: {
      stocks() {
        return this.$store.getters.stocks;
      }
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
