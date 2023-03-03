<script>
export default{
    props:{
        card:{
            type: Object,
            required: true,
        }
    }
}
</script>

<template>
    <li>
        <img :src="card.card_images[0].image_url" alt="">
        <p class="card-title">{{ card.name }}</p>
        <p class="card-archetype">{{ card.archetype }}</p>
    </li>
</template>

<style>

.card-title{
    text-align: center;
    text-transform: uppercase;
    font-weight: 600;
    margin-top: 20px;
    font-size: 20px;
    padding: 0 8px;
}

.card-archetype{
    text-align: center;
    margin-top: 20px;
    font-size: 20px;
}
</style>