<template>
    <div>
        <img :src="room.image" class="room-img">
        <h4 @click="$emit('openModal')">{{room.title}}</h4>
        <p>{{room.price}}원</p>
        <p>{{room.content}}</p>
    </div>
</template>

<script>
export default {
    name : 'listCard',
    props :{
        room : Object,
    } 

}
</script>

<style>

</style>