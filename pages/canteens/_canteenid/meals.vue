<template>
  <div class="container">
    <div>
      <h1>Mahlzeiten</h1>
      <ul class="meals">
        <li class="meal" v-for="(meal, index) in meals" :key="index">
          <div>{{ meal.name }}</div>
          <div>{{ meal.category }}</div>
          <div><ul><li class="price" v-for="(price, index) in meals.prices" :key="index">{{price}}</li></ul></div>
          <div>{{ meal.prices }}</div>
          <div>{{ meal.notes }}</div>
        </li>
      </ul>
      <p>
        <nuxt-link to="/canteens" class="button--grey">Back to canteens</nuxt-link>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({ params }) {
    if (params.canteenid && params.day) {
      // `https://openmensa.org/api/v2/canteens/${params.id}/days/${params.day}/meals`)
      return axios
        .get(`https://openmensa.org/api/v2/canteens/${params.canteenid}/days/${params.day}/meals`)
        .then(res => {
          return { meals: res.data };
        });
    } else {
      return axios
        .get(`https://openmensa.org/api/v2/canteens/${params.canteenid}/days/${params.day}/meals`)
        .then(res => {
          return { meals: res.data };
        });
      // return {
      //   meals: [
      //     {
      //       name: "test-name",
      //       category: "test-category",
      //       notes: ["test1", "test2"]
      //     }
      //   ]
      // };
    }
  }
};
</script>
