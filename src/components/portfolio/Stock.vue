<template>
  <div class="card">
    <div class="card-header text-primary">
      <h3 class="card-title">
        {{ stock.name }}
        <small>(Price: {{ stock.price }} | Quantity: {{ stock.quantity }})</small>
      </h3>
    </div>
    <div class="card-body text-primary">
      <div class="pull-left">
        <input
          type="number"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
        >
      </div>
      <div class="pull-right">
        <button
          class="btn btn-primary"
          @click="sellStock"
          :disabled="quantity<=0 || !Number.isInteger(quantity)"
          >Sell</button>
      </div>
    </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
    data() {
      return {
        quantity: 0
      }
    },
    props: ['stock'],
    methods: {
      ...mapActions({
        placeSellOrder: 'sellStock'
      }),
      sellStock() {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        this.placeSellOrder(order);
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
</style>
