<template>
  <div class="home">
    <div class="header">
        <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="">

        <div class="wrapper--input">
            <input v-model="user_search_restaurant" type="text" placeholder="De quoi avez vous envie ?">
            <div class="search">
                <router-link to="/restaurant">
                    <div v-for="(restaurant, i ) in search_restaurant" :key="i" class="contenair--restaurant--search">
                        <div class="wrapper--img">
                            <img :src="restaurant.image" alt="">
                        </div>
                        <p>{{  restaurant.name  }}</p>
                    </div>
                </router-link>
            </div>
        </div>

    </div>
    <div class="banner"></div>
    <!-- <h2 class="title">
        Nos restaurant
    </h2> -->
    <RestaurantRow v-for="(data , i) in data_restaurant" :key="i" :three_restaurant="data"/>
  </div>
</template>

<script>
// IMPORT
import { info } from '../BDD.js'
import { onMounted , ref , watch } from 'vue'

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

        let data_restaurant = ref([]);
        let all_restaurant = []

        const makeDataRestaurant = ( ) => {
            let three_restaurant = [];

            for (const restaurant of info) {
                const new_restaurant = new Restaurant (restaurant.name, restaurant.note, restaurant.image ,restaurant.drive_time)

                // Make all restaurant array 
                all_restaurant.push(new_restaurant)

                if (three_restaurant.length == 2) {
                    three_restaurant.push(new_restaurant);
                    data_restaurant.value.push(three_restaurant);
                    three_restaurant = [];
                }else {
                    three_restaurant.push(new_restaurant);
                }
            }
        }

        // User searh restaurant
        let user_search_restaurant = ref('');
        let search_restaurant = ref([]);

        watch(user_search_restaurant , new_value => {
            let regex = RegExp(new_value.toLowerCase());

            let new_search_restaurant = all_restaurant.filter(restaurant => regex.test(restaurant.name.toLowerCase()));    
            
            new_value == 0 ? search_restaurant.value = [] : search_restaurant.value = new_search_restaurant;
        })
        //

        onMounted(makeDataRestaurant);

        return {
            data_restaurant,
            user_search_restaurant,
            search_restaurant,
        }
    }

}
</script>

<style lang="scss">
    .home {
        .header {
            height: 120px;
            width: 100%;
            display: flex;
            align-items: center;
            justify-content: space-between;

            img {
                width: 200px;
            }

            .wrapper--input {
                position: relative;
                input {
                    background: #f6f6f6;
                    border: none;
                    height: 60px;
                    width: 400px;
                    outline: none;
                    padding-left: 20px;
                }

                .search {
                    position: absolute;
                    top: 100%;
                    width: 100%;
                    background-color: #fff;

                    .contenair--restaurant--search {
                        display: flex;
                        align-items: center;
                        padding: 10px;

                        &:hover {
                            background: #f6f6f6;
                        }

                        .wrapper--img {
                            height: 60px;
                            width: 60px;
                            margin-right: 25px;
                            border-radius: 50%;
                            overflow: hidden;

                            img {
                                height: 100%;
                                width: 100%;
                            }
                        }
                    }
                }
            }

        }

        .banner {
            height: 200px;
            width: 100%;
            background-image: url("https://g7y6h3a7.rocketcdn.me/wp-content/uploads/2020/05/travailler-uber-eats.jpg");
            background-size: cover;
            background-position: top  center;
        }

        // .title {
        //     font-size: 2rem;
        // }
    }
</style>