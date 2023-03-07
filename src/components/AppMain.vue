<script>
import axios from 'axios'
import AppCard from './AppCard.vue'
import {store} from '../store'
import Filters from './Filters.vue'
export default{
    components:{
        AppCard,
        Filters,
    },

    data(){
        return{
            store
        }
    },

    methods:{
        fetchCards(){
            const search = this.store.nameCard
            const numSelected = this.store.numCard
            console.log(this.store, numSelected)
            axios.get( `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0`,{
                params:{
                    fname: search,
                    num: numSelected
                }
            })
            .then((res) => {
                console.log(res)
                this.store.cards = res.data.data
                console.log(this.store)
            }).catch((error)=>{
                this.store.cards=[]
            })
        },
    },

    created(){
        this.fetchCards()
    }
}
</script>

<template>
    <main>
        <div class="container">
            <div>
                <Filters @onSearch="fetchCards" @changeNumCard="fetchCards"/>
            </div>

            <div class="num-card">
                <p>Found: {{ store.cards.length }}</p>
            </div>
            <!--<ul class="row list-cards">
                <li v-for="(element, index) in cards" >
                    <img :src="element.card_images[0].image_url" alt="">
                    <p class="card-title">{{ element.name }}</p>
                </li>
            </ul>-->
            <ul class="row list-cards">
                <AppCard v-for="element in store.cards" :key="element.id" :card="element"/>
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

.num-card{
    padding: 20px;
    background-color: black;
    color: white;

    p{
        font-size: 20px;
    }
}
</style>