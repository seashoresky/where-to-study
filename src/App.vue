<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class = "background">
    <div class = "title">今天去哪学</div>
    <div class = "container">
      <div class = "position">{{position}}</div>
      <div class = "description">{{description}}</div>
    </div>
    <button class = "button" @click="getPosition()">开roll！</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        position: "NULL",
        description: "none",
        positions: ["东教", "西教", "北教", "启真湖底", "管院楼顶", "小剧场b217"],
        descriptions: ["经典永不过时", "幸运的人不会遇到情侣", "误入老狗们的世界", "咕噜咕噜", "一跃解……", "凭此截图获取一天潮人体验券"],
      }
    },
    methods: {
      getPosition(){
        const total = this.positions.length;
        let i = Math.floor(Math.random()*total);
        this.position = this.positions[i];
        this.description = this.descriptions[i];
      }
    }
  }
</script>

<style scoped>
.background{
  border: 1px solid;
  display: flex;
  flex-direction: column;
  text-align: center;
	justify-content: center;
	align-items: center;
  min-width: 500px;
}
.title{
  font-weight: 500;
	font-size: 22px;
	line-height: 24px;
	display: flex;
	text-align: center;
	justify-content: center;
	align-items: center;
}
.container{
  display: flex;
  text-align: center;
	justify-content: center;
	align-items: center;
  margin-top: 200px;
  margin-bottom: 200px;
  flex-direction: column;
  width: 100%;
}
.position{
  display: flex;
  font-weight: 500;
	font-size: 22px;
	line-height: 24px;
  margin-bottom: 50px;
}
.description{
  display: flex;
	font-size: 18px;
	line-height: 24px;
}
.button{
  display: flex;
	flex-direction: row;
	font-weight: 500;
	font-size: 22px;
	line-height: 28px;
	align-items: center;
	text-align: center;
	justify-content: center;
  border-radius: 82px;
  background: #718DF7;
  color: #FFFFFF;
  border: none;
  width: 150px;
}
</style>
