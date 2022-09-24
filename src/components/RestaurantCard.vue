<template>
<div class="restaurant--card">
  <div :style="changeBackground()" class="restaurant--img">
  </div>
  <div class="restaurant--informations">
    <div class="restaurant--title">
      <p class="name">{{ restaurantInfo.name }}</p>
      <p class="review">
        <sCardpan> {{ restaurantInfo.review }}</sCardpan>
      </p>
    </div>
    <div class="restaurant--estimation-time">{{ restaurantInfo.drive_time }}</div>
  </div>

</div>

</template>

<script>

import {Restaurant} from "@/models/Restaurant";

export default {
  name: "RestaurantCard",
  props:{
    restaurantInfo:Restaurant
  },
  setup(props){

    const changeBackground =() =>{
      return {
        backgroundImage: `url(${props.restaurantInfo.image})`
      }
    };

    return {
      changeBackground
    }
  }
}
</script>

<style scoped lang="scss">
.restaurant--card{
  width: 32%;
  height: 30vh;

  p:{
    margin: 0px;
  }
  .restaurant--img{
    height: 70%;
    background-size: cover;
    background-position: center;
  }
  .restaurant--informations{

    .restaurant--title{
      display: flex;
      margin-bottom: 5px;
      align-items: center;
      justify-content: space-between;
      p.name{
        margin-top: 5px;
        margin-bottom: 1px;
      }
      p.review{
        margin-top: 5px;
        margin-bottom: 1px;
        background-color: #eeeeee;
        border-radius: 50%;
        height: 30px;
        width: 30px;
        display: flex;
        align-items: center;
        font-size: 0.8rem;
        font-weight: bold;
        span {
          padding: 5px;
          margin-top: 2px;
          margin-bottom: 2px;
        }
      }
    }
    .restaurant--estimation-time{
      font-size: 0.9rem;
    }
  }
}
</style>