<template>
  <div class="container">
    <div>
      <h1>Kantinen</h1>
      <ul>
        <li v-for="(canteen, index) in canteens" :key="index">
          <NuxtLink :to="{ name: 'canteens-canteenid-meals', params: {canteenid: canteen.id, day: '2021-08-27' } }">
          {{ canteen.name }}
        </NuxtLink>
          <NuxtLink :to="{ name: 'canteens-id', params: { id: canteen.id,name:canteen.name, address: canteen.address } }">
          {{ canteen.id }}
        </NuxtLink>
        </li>
      </ul>
      <p>
        <nuxt-link to="/" class="button--grey">Back home</nuxt-link>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  asyncData({ params }) {
      return axios.get(`https://openmensa.org/api/v2/canteens`).then(res => {
        return { canteens: res.data };
      });
  }
};
</script>
