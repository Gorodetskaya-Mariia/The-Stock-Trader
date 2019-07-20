<template>
  <div class="card">
    <div class="card-header text-primary">
      <h3 class="card-title">
        {{ stock.name }}
        <small>(Price: {{ stock.price }})</small>
      </h3>
    </div>
    <div class="card-body text-primary">
      <div class="pull-left">
        <input
          type="number"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
          :class="{ danger: insufficientFunds }"
        >
      </div>
      <div class="pull-right">
        <button
          class="btn btn-primary"
          @click="buyStock"
          :disabled="insufficientFunds || quantity<=0 || !Number.isInteger(quantity)"
          >{{ insufficientFunds ? 'Insufficient Funds' : 'Buy'}}</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds;
      },
      insufficientFunds() {
        return this.quantity * this.stock.price > this.funds;
      }
    },
    methods: {
      buyStock() {
        const order = {
          stockId: this.stock.id,
          // stockName: this.stock.name,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        this.$store.dispatch('buyStock', order);
        this.quantity = 0;
      }
    }
  }
</script>

<style>
  .card {
    width: 48%;
    padding: 15px;
    margin-bottom: 40px;
    border: 1px solid #337ab7;
    border-radius: 5px;
  }

  .card-header {
    margin-bottom: 15px;
  }

  .danger {
    border: 1px solid red;
  }
</style>
