<template>
  <nav class="navbar">
    <ul class="nav nav--left">
         <router-link to="/" tag="li" class="navbar-brand" active-class="active">
            <a><strong>Stock Trader</strong></a>
        </router-link>
          <router-link to="/portfolio" tag="li" active-class="active">
            <a>Portfolio</a>
          </router-link>
          <router-link to="/stocks" tag="li" active-class="active">
            <a>Stocks</a>
          </router-link>
        </ul>
        <ul class="nav nav-right">
           <li>
                <a href="#" @click="endDay">End Day</a>
          </li>
            <li class="dropdown"
              :class="{open: isDropdownOpen}"
              @click="isDropdownOpen = !isDropdownOpen">
            <a href="#"
              class="dropdown-toggle"
              data-toggle="dropdown"
              role="button"
              aria-haspopup="true"
              aria-expanded="false">Save & Load <span class="caret"></span>
            </a>
            <ul class="dropdown-menu">
              <li active-class="active">
                <a href="#" @click="saveData">Save Data</a>
              </li>
              <li active-class="active">
                <a href="#" @click="loadData">Load Data</a>
              </li>
            </ul>
          </li>
          <li>
            <strong>Funds: {{ funds | currency }}</strong>
          </li>
        </ul>
  </nav>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
    data() {
      return {
        isDropdownOpen: false
      }
    },
    computed: {
      funds() {
        return this.$store.getters.funds;
      }
    },
    methods: {
      ...mapActions({
        randomizeStocks: 'randomizeStocks',
        fetchData: 'loadData'
      }),
      endDay() {
        this.randomizeStocks();
      },
      saveData() {
        const data = {
          funds: this.$store.getters.funds,
          stockPortfolio: this.$store.getters.stockPortfolio,
          stocks: this.$store.getters.stocks
        };
        this.$http.put('data.json', data);
      },
      loadData() {
        this.fetchData();
      }
    }
  }
</script>

