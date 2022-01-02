<template>
  <table class="table table-dark">
    <thead>
      <tr>
        <th v-for="title in cryptoTitleArr" :key="title">{{ title }}</th>
      </tr>
    </thead>

    <tbody>
      <tr v-for="(crypto, index) in cryptoArr" :key="crypto.id">
        <td>{{ index }}</td>
        <td>
          <img :src="crypto.image" style="width: 2rem" alt="crypto-img" />
          <span>
            {{ crypto.name }}
          </span>
          <span class="ms-2 text-uppercase text-muted">
            {{ crypto.symbol }}
          </span>
        </td>
        <td>
          ${{ crypto.current_price }}
        </td>
        <td>
          {{ crypto.price_change_percentage_24h }}
        </td>
        <td>
          {{ crypto.total_volume }}
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    cryptoArr: {
      type: Array,
      required: true,
    },
    cryptoTitleArr: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style></style>
