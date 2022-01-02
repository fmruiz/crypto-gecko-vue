<template>
  <div class="container">
    <div class="row">
      <h1>CRYPTO GECKO!</h1>
      <CryptoTable :cryptoArr="cryptos" :cryptoTitleArr="titles" />
    </div>
  </div>
</template>

<script>
import CryptoTable from "./components/CryptoTable.vue";
export default {
  components: { CryptoTable },
  name: "App",
  data() {
    return {
      cryptos: null,
      titles: ["#", "Coin", "Price", "Price Change", "24h Volume"],
    };
  },
  async mounted() {
    // API get data
    const res = await fetch(
      "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false"
    );
    const data = await res.json();
    this.cryptos = data;
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
