<script>
import { createDOMCompilerError } from '@vue/compiler-dom'
import { onMounted } from 'vue'
import axios from 'axios'
export default{
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
            <ul class="row list-cards">
                <li v-for="(element, index) in cards" >
                    <img :src="element.card_images[0].image_url" alt="">
                    
                </li>
            </ul>
        </div>
    </main>
</template>

<style scoped lang="scss">
@use './style/partials/variable.scss';

.list-cards{
    flex-wrap: wrap;
    gap: 30px;

    li{
        width: calc(100% / 5 - 120px / 5);
    }
}
</style>