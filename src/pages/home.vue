<template>
  <div class="home">
    <div class="header">
    <img src="../assets/logo.svg" alt="logo ubereats" />
    <input class="search" type="text" placeholder="De quoi avez vous envie ?"/>
    </div>
    <div class="banniere" />
    <restaurant-row v-for="(data, index) in dataRestaurant" :key="index" :rowRestaurant="data"/>

  </div>

</template>

<script>
import BDD from "@/BDD";
import {Restaurant} from "@/models/Restaurant";

import RestaurantRow from "@/components/RestaurantRow";
import {onMounted, ref} from "vue";

export default {
  name: 'HomeComponent',
  components: {
    RestaurantRow,
  },

  setup() {
    let dataRestaurant = ref([]);

    const makeDataRestaurant = () => {
      let dataRow = []
      for (const restaurant of BDD) {
        dataRow.push(new Restaurant(restaurant.name, restaurant.review, restaurant.image, restaurant.drive_time));
        if (dataRow.length >= 3) {
          dataRestaurant.value.push(dataRow);
          dataRow = [];
        }

      }
    };

    onMounted(makeDataRestaurant);

    return {
      dataRestaurant
    };
  }
}
</script>

<style scoped lang="scss">
.header{
  height: 5vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-bottom: 20px;
  img{
    width:200px;
  }
  input{
    background-color: #f6f6f6;
    width: 20%;
    border: none;
    height: 6vh;
    outline: none;
    padding-left: 20px;
  }

}
.banniere{
  background-image: url("../assets/banniere.png");
  background-position: center center;
  background-size: cover;
  background-repeat: no-repeat;
  width: 100%;
  height: 25vh;
  padding-top: 10px;


}

</style>