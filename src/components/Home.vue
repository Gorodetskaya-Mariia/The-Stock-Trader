<template>
  <div>
    <p>You can buy as many stocks as you can afford on the page "Stocks".</p>
    <p>On page "Portfolio" you can see all stocks which you have bought.</p>
    <p>Also, you may <span>Save</span> and <span>Load</span> your data.</p>
    <p>Click on "End Day" to recieve updated prices of every stock. You may sell your stocks and get a profit.</p>
    <hr>
    <strong>Your Funds: {{ funds | currency }}</strong>
  </div>
</template>

<script>
  export default {
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    }
  }
</script>
