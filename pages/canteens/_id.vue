<template>
  <div class="container">
    <div>
      <h1>{{canteen.name}}</h1>
      <p>{{canteen.address}}</p>
      <ul>
        <li v-for="(day, index) in days" :key="index">
          <NuxtLink :to="{ name: 'canteens-id', params: { canteenid: canteen.id, day: {day} } }">
          {{ canteen.name }}
        </NuxtLink>
        </li>
      </ul>
      <p>
        <nuxt-link to="/canteens/canteen" class="button--grey">Back home</nuxt-link>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  asyncData({ params }) {
      return axios
        .get(`https://openmensa.org/api/v2/canteens/${params.id}/days`)
        .then(res => {
          return { days: res.data };
        });
  }
};
</script>