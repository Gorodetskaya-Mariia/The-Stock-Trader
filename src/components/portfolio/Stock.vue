<template>
  <div class="card">
    <div class="card-header">
      <h3 class="card-title">
        {{ stock.name }}
      </h3>
      <p>(Price: {{ stock.price }} | Quantity: {{ stock.quantity }})</p>
    </div>
    <div class="card-body">
      <div class="pull-left">
        <input
          type="number"
          class="form-control"
          placeholder="Quantity"
          v-model.number="quantity"
          :class="{ danger: insufficientStocks }"
        >
      </div>
      <div class="pull-right">
        <button
          class="btn"
          @click="sellStock"
          :disabled="insufficientStocks || quantity<=0 || !Number.isInteger(quantity)"
          >{{ insufficientStocks ? 'Not enough Stocks' : 'Sell'}}</button>
      </div>
    </div>
  </div>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
    props: ['stock'],
    data() {
      return {
        quantity: 0
      }
    },
    computed: {
      insufficientStocks() {
        return this.quantity > this.stock.quantity;
      }
    },
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
