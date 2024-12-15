<template>
    <div class="black-bg" v-if="modalState == true">
    <div class="white-bg">
        <img :src="rooms[roomNumber].image">
        <h4>{{rooms[roomNumber].title}}</h4>
        <p>{{rooms[roomNumber].content}}</p>
        <p>{{rooms[roomNumber].price}}원</p>
        <Discount/>
<!-- <button @click="modalState = false">닫힘</button> -->
<!-- (주의) props는 등호로 재할당 같은것 불가.
        read-only임 받아온거 수정하면 큰일남 -->
    </div>
    </div>

</template>

<script>
export default {
    name : 'ModalComponent',
    props : {
        rooms : Array, //받아온 데이터의 자료형 이름을 대문자로
        roomNumber : Number,
        modalState : Boolean,
    }

}
</script>

<style>

</style>