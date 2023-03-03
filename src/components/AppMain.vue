<script>
import axios from 'axios'
import AppCard from './AppCard.vue'
export default{
    components:{
        AppCard
    },

    data(){
        return{
            cards:[]
        }
    },

    methods:{
        fetchCards(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0')
            .then((res) => {
                console.log(res)
                this.cards = res.data.data
                console.log(this.cards)
            })
        }
    },

    created(){
        this.fetchCards()
    }
}
</script>

<template>
    <main>
        <div class="container">
            <!--<ul class="row list-cards">
                <li v-for="(element, index) in cards" >
                    <img :src="element.card_images[0].image_url" alt="">
                    <p class="card-title">{{ element.name }}</p>
                </li>
            </ul>-->
            <ul class="row list-cards">
                <AppCard v-for="element in cards" :key="element.id" :card="element"/>
            </ul>
        </div>
    </main>
</template>

<style scoped lang="scss">
@use '../style/partials/variable.scss';

main{
    background-color: #D48F38;
}
.container{
    padding: 70px;
    background-color: white;
}
.list-cards{
    flex-wrap: wrap;
    gap: 30px;

    li{
        width: calc(100% / 5 - 120px / 5);
        background-color: #D48F38;
        padding-bottom: 15px;
    }
}
</style>