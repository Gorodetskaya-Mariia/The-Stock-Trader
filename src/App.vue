<template>
    <div class="container">
      <app-header></app-header>
      <div class="content">
        <transition name="slide" mode="out-in">
          <router-view></router-view>
        </transition>
      </div>
    </div>
</template>

<script>
    import Header from './components/Header.vue'

    export default {
      components: {
        appHeader: Header
      },
      created() {
        this.$store.dispatch('initStocks');
      }
    }
</script>
