<template>
  <nav class="navbar navbar-default">
    <div class="container-fluid">
      <div class="navbar-header">
        <router-link to="/" class="navbar-brand" active-class="active" exact>
            <a>Stock Trader</a>
        </router-link>
      </div>
      <div class="collapse navbar-collapse">
        <ul class="nav navbar-nav">
          <router-link to="/portfolio" tag="li" active-class="active">
            <a>Portfolio</a>
          </router-link>
          <router-link to="/stocks" tag="li" active-class="active">
            <a>Stocks</a>
          </router-link>
        </ul>
        <strong class="nav-text navbar-right">Funds: {{ funds | currency }}</strong>
        <ul class="nav navbar-nav navbar-right">
          <li><a href="#">End Day</a></li>
          <li class="dropdown">
            <a href="#"
              class="dropdown-toggle"
              data-toggle="dropdown"
              role="button"
              aria-haspopup="true"
              aria-expanded="false">Save & Load <span class="caret"></span>
            </a>
          </li>
        </ul>
        <ul class="dropdown-menu">
          <li><a href="#">Save Data</a></li>
          <li><a href="#">Load Data</a></li>
        </ul>
      </div>
    </div>
  </nav>
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

