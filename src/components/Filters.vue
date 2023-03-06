<script>
import {store} from '../store'

export default{
    data(){
        return{
            store
        }
    }
}
</script>

<template>
    <input class="search-bar" type="text" placeholder="Name card..." @keyup.enter="$emit('onSearch')" v-model="store.nameCard">
    <select id="" @change="$emit('changeNumCard')" v-model="store.numCard">
        <option value="">20</option>
        <option value="">50</option>
        <option value="">100</option>
    </select>
</template>

<style>
    .search-bar, select{
        margin-bottom: 30px;
        padding: 10px;
        border-radius: 20px;
    }

    select {
        margin-left: 20px;
    }

</style>