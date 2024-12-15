<template>

  <!-- <div class="black-bg" v-if="modalState == true">
    <div class="white-bg">
      <img :src="rooms[roomNumber].image">
      <h4>{{rooms[roomNumber].title}}</h4>
      <p>{{rooms[roomNumber].content}}</p>
      <p>{{rooms[roomNumber].price}}원</p>
      <Discount/>
      <button @click="modalState = false">닫힘</button>
    </div>
  </div> -->



  <Modal :rooms = "rooms" :roomNumber = "roomNumber" :modalState = "modalState"/>
  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <Discount v-bind="오브젝트"/>

  
  
  <!-- <div v-for="(a,i) in products" :key="i">
    <h4>{{a}}</h4>
    <p>가격상관없음</p>
    <button @click="increase"> 허위매물 신고 </button> <span>신고수: {{count[i]}}</span>
  </div> -->

  <!-- <div>
    <img src="./assets/room0.jpg" class="room-img">
    <h4 @click="modalState = true">{{products[0]}}</h4>
    <p>50만원</p>
    <button @click="count[0]++"> 허위매물 신고 </button> 
    <span>신고수: {{count[0]}}</span>
  </div> -->


  <Card @openModal="modalState=true"
  :room = 'rooms[i]' v-for="(room,i) in rooms" :key="i"/>

  <!-- <div v-for="(a,i) in rooms" :key="i">
    <img :src="a.image" class="room-img">
    <h4 @click="modalState=true; roomNumber=i">{{a.title}}</h4>
    <p>{{a.price}}원</p>
    <p>{{a.content}}원</p>
  </div> -->



  
</template>
    
<script>
import data from './oneroom.js';
import DiscountBanner from './Discount.vue'; //자유롭게 작명
import ModalComponent from './Modal.vue'
import listCard from './Card.vue'

export default {
  name: 'App',
  data(){
    return {
      roomNumber: 0,
      rooms : data,
      modalState: false,
      메뉴들: ['Home', 'Shop', 'About'],
      count: [0, 0, 0],
      price1: 60,
      price2: 70,
      blue: 'color: blue',
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      
    }
  },
  methods:{
    increase(){
      this.count++;
    }
  },
  components: {
    Discount : DiscountBanner, 
    //왼쪽은 자유작명
    //Discount,  << es6 신문법
    Modal : ModalComponent,
    Card : listCard,
  }
}
</script>

<style>
body {
  margin: 0
}
div {
  box-sizing: border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}


.room-img{
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
