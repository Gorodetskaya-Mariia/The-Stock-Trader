<template>
  <div>
    <h1>Trade or View your Portfolio</h1>
    <h2>You may Save and Load your Data</h2>
    <h2>Click on 'End Day' to began a New Day!</h2>
    <hr>
    <p>Your Funds: {{ funds | currency }}</p>
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
