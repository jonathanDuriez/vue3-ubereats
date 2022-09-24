<template>
  <div class="restaurant--row">
    <h2 class="title">
      Nos Restaurants
    </h2>
    <div class="row">
      <restaurant-card v-for="(data, index) in rowRestaurant" :key="index" :restaurantInfo="data"/>
    </div>
  </div>

</template>

<script>

import RestaurantCard from "@/components/RestaurantCard.vue";
export default {
  name: "RestaurantRow",
  components: {
    RestaurantCard
  },
  props: {
    rowRestaurant:[]
  }


}
</script>

<style scoped lang="scss">
.restaurant--row{
  .title{
    font-size: 2rem;
  }
  .row {
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: space-between;
  }
}

</style>