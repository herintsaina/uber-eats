<template>
  <div class="restaurant--card">
    <div  class="restaurant--image">
      <img :src="info_restaurant.image" alt="">
    </div>  
    <div class="restaurant--information">
      <div class="top">
        <p class="name">
          {{ info_restaurant.name }}
        </p>
        <p class="note">
          {{ info_restaurant.note }}
        </p>
      </div>
      <p class="time">
        {{ info_restaurant.drive_time }}
      </p>
    </div>
  </div>
</template>

<script>
// import 
// import { computed } from 'vue'
export default {
  name: "RestaurantCard",

  props: {
    info_restaurant : Object,
  },
  // setup(props) {
  //   // const changeBackground = computed(() =>{
  //   //   return {
  //   //   backgroundImage : `url(${props.info_restaurant.image})`
  //   //   }
  //   // })

  //   // console.log(changeBackground());

  //   // // return 
  //   // return {
  //   //   changeBackground
  //   // }
    
  // }

}
</script>

<style lang="scss">
    .restaurant--card{
        width: 32%;
        height: 35vh;

        p{
          margin: 0px;
        }

        .restaurant--image {
            // background-image: url("https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw==");
            height: 70%;
            
            background-size: cover;
            background-position: center;

            img{
              height: 100%;
              width: 100%;
              object-fit: cover;
            }
        }

        .restaurant--information{
          
          .top {
            margin: 5px 0px;
            display: flex;
            align-items: center;
            justify-content: space-between;

            

            .note{
              background-color: #eeeeee;
              display: flex;
              justify-content: center;
              align-items: center;
              height: 30px;
              width: 30px;
              font-size: 0.8rem;
              border-radius: 50%;
            }
          }

          .time{
            font-size: 0.9rem;
          }
        }
    }
</style>