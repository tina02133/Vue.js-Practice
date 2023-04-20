<template>

  <!-- 모달창 부분 ==> v-if = "true"일때에만 html보여줌 -->
  <div class="black-bg" v-if="모달창열렸니==true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니=false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="작명 in 메뉴들" :key="작명">{{ 작명 }}</a>
  </div>


  <!-- HTML 태그안의 속성 데이터바인딩은 :어쩌구 -->
  <!-- HTML 태그안의 내용 데이터바인딩은 {{어쩌구}} -->
  <div v-for="(item, i) in 원룸들" :key="i">
    <img @click="모달창열렸니=true"  class="room-img" :src="원룸들[i].image">
    <h3>{{원룸들[i].title}}</h3>
    <p>{{원룸들[i].price}}</p>
    <button @click="increase(i)">허위매물신고</button> <span>신고 수 : {{신고수[i]}}</span>
  </div>

   
</template>

<script>
import data from './assets/oneroom.js'
data;


export default {
  name: "App",
  data() {
    return {
      메뉴들: ["Home", "Shop", "About"],
      // products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      신고수: [0,0,0],
      모달창열렸니 : false,
      원룸들 : data,
    };
  },
  methods : {
    increase(i){
      this.신고수[i]++;
    }
    
  },
  components: {},
};
</script>

<style>
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
  padding: 15px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
  padding: 20px;

}

/* 모달창 ui 만들기 */
body{
  margin: 0;
}

div{
  box-sizing: border-box;
}

.black-bg{
  width: 100%; height: 100% ;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}

.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}



</style>
