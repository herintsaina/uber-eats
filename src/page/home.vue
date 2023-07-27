<template>
  <div class="home">
    <restaurant-row />
  </div>
</template>

<script>
// IMPORT
import { info } from '../BDD.js'
import { onMounted } from 'vue'

// COMPONENT
import RestaurantRow from '../components/RestaurantRow.vue';

export default {
    name: 'Home', 

    components: {
        RestaurantRow,
    },

    setup() {
        class Restaurant {
            constructor (name , note, image,drive_time ) {
                this.name = name
                this.note = note
                this.image = image
                this.drive_time = drive_time 
            }
        }

        let data_restaurant = []

        const makeDataRestaurant = ( ) => {
            let three_restaurant = [];

            for (const restaurant of info) {
                const new_restaurant = new Restaurant (restaurant.name, restaurant.note, restaurant.image ,restaurant.drive_time)

                if (three_restaurant.length == 2) {
                    three_restaurant.push(new_restaurant);
                    data_restaurant.push(three_restaurant);
                    three_restaurant = [];
                }else {
                    three_restaurant.push(new_restaurant);
                }
            }
        }
        onMounted(makeDataRestaurant);
    }

}
</script>

<style>

</style>