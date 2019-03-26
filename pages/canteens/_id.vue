<template>
  <div class="container">
    <div>
      <h1>{{name}}</h1>
      <p>{{address}}</p>
      <ul>
        <li v-for="(day, index) in days" :key="index">
          <NuxtLink
            :to="{ name: 'canteens-id', params: { canteenid: cid, day: day.date } }"
          >{{ days.date}}</NuxtLink>
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
        return { days: res.data, name: params.name, address: params.address, cid:params.id };
      });
  }
};
</script>