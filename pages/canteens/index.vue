<template>
  <div class="container">
    <div>
      <h1>Kantinen</h1>
      <ul>
        <li v-for="(canteen, index) in canteens" :key="index">
          <NuxtLink :to="{ name: 'canteens-meals-id', params: { canteenid: canteen.id, day: '2019-03-25' } }">
          {{ canteen.name }}
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