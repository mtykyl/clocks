<template>
<div class="container">
  <div class="clock">
    <div class="date">
      <p>{{ year }}{{ month }}{{ day }}</p>
    </div>
    <div class="time">
      <p>
        {{ hour }}:{{ minites }}:<span class="seconds">{{ seconds }}</span>
      </p>
    </div>
    <div class="button" v-on:click="message">
      <p>アラーム機能追加</p>
    </div>
  </div>
</div>
</template>
<script>
export default{
  name:"Clock-screen",
  data(){
    return{
      //日時を表示
      date:new Date(),
    };
  },
  computed:{
    //year
    year(){
      return this.date.getFullYear();
    },
    //month
    month(){
      return this.date.getMonth() +1;
    },
    //day
    day(){
      return this.dateTimePadding(this.date.getDate());
    },
    //hour
    hour(){
      return this.dateTimePadding(this.date.getHours());
    },
    //minute
    minites(){
      return this.dateTimePadding(this.date.getMinutes());
    },
    //second
    seconds(){
      return this.dateTimePadding(this.date.getSeconds());
    }
  },
  mounted(){
    //先にmountedが動いて表示される
    this.setDate();
    //１秒ごとにsetDate()を実行
    setInterval(()=>this.setDate(),1000);
  },
  methods:{
    //日時を２桁にする
    dateTimePadding(num){
      return("0" + num).slice(-2);
    },
    //現在の時刻を取得する
    setDate(){
      this.date=new Date();
    },
    message(){
      window.setTimeout(()=>{
        alert("10秒経過");
      },10000)
    },
  }
}
</script>
<style scoped>
.container{
  height:100%;
  display:flex;
  flex-flow:column;
  justify-content: center;
  align-items: center;
  background-color: #262626;
}
p{
  margin: 0px;
}
.date,
.time{
  font-weight: 700;
  color: #00ff01;
  font-size:70px;
}
.date{
  font-size: 16px;
  text-align: center;
}
.button{
  border:1px solid white;
  text-align: center;
  padding: 10px 0;
  color: white;

}
</style>
