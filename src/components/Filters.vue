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
    <input type="text" placeholder="Name card..." @keyup.enter="$emit('onSearch')" v-model="store.nameCard">
</template>

<style>

</style>