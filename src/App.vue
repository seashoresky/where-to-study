<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="background">
    <div class="top-bar">
      <div class="title">今天去哪学📚</div>
      <button class="menu">
        <svg width="36" height="36" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g clip-path="url(#clip0_14_111)">
            <path d="M11.115 12.885L18 19.755L24.885 12.885L27 15L18 24L9 15L11.115 12.885Z" fill="black" />
          </g>
          <defs>
            <clipPath id="clip0_14_111">
              <rect width="36" height="36" fill="white" />
            </clipPath>
          </defs>
        </svg>
        紫金港</button>
    </div>
    <div class="picker">
      <div class="picker-list">
        <h2>想在什么方位</h2>
        <ul>
          <li>东</li>
          <li>西</li>
          <li>南</li>
          <li>北</li>
        </ul>
      </div>
      <div class="picker-map">
      </div>
    </div>
    <div class="picker">
      <div class="picker-list">
        <h2>想要什么氛围</h2>
        <ul>
          <li>人迹罕至</li>
          <li>清静恬淡</li>
          <li>卷王密布</li>
          <li>烟火气息</li>
          <li>另辟蹊径</li>
        </ul>
      </div>
    </div>
    <div class="container">
      <div class="caption">
        <div></div>
        <h1>今天去🚀</h1>
        <div class="help">
          <svg width="30" height="30" viewBox="0 0 30 30" fill="none" xmlns="http://www.w3.org/2000/svg">
            <g clip-path="url(#clip0_14_158)">
              <path
                d="M15 2.5C8.1 2.5 2.5 8.1 2.5 15C2.5 21.9 8.1 27.5 15 27.5C21.9 27.5 27.5 21.9 27.5 15C27.5 8.1 21.9 2.5 15 2.5ZM16.25 23.75H13.75V21.25H16.25V23.75ZM18.8375 14.0625L17.7125 15.2125C16.8125 16.125 16.25 16.875 16.25 18.75H13.75V18.125C13.75 16.75 14.3125 15.5 15.2125 14.5875L16.7625 13.0125C17.225 12.5625 17.5 11.9375 17.5 11.25C17.5 9.875 16.375 8.75 15 8.75C13.625 8.75 12.5 9.875 12.5 11.25H10C10 8.4875 12.2375 6.25 15 6.25C17.7625 6.25 20 8.4875 20 11.25C20 12.35 19.55 13.35 18.8375 14.0625Z"
                fill="#ECECEC" />
            </g>
            <defs>
              <clipPath id="clip0_14_158">
                <rect width="30" height="30" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </div>
      </div>
      <div class="pick">
        <div class="position">{{position}}</div>
        <div class="icon">{{icon}}</div>
        <div class="description">{{description}}</div>
      </div>
      <button class="button" @click="getPosition()">开roll！</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      position: "NULL",
      description: "none",
      positions: ["东教", "西教", "北教", "启真湖底", "管院楼顶", "小剧场b217"],
      icons: ["🏫", "💑", "🧑‍🎓", "🤿", "🏢", "🎭"],
      descriptions: ["经典永不过时", "幸运的人不会遇到情侣", "误入老狗们的世界", "咕噜咕噜", "一跃解……", "凭此截图获取一天潮人体验券"],
    }
  },
  methods: {
    getPosition() {
      const total = this.positions.length;
      let i = Math.floor(Math.random() * total);
      this.position = this.positions[i];
      this.description = this.descriptions[i];
      this.icon = this.icons[i];
    }

  }
}
</script>

<style scoped>
* {
  font-family: "Noto Sans SC";
}

.background {
  border: 1px solid;
  position: relative;
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: flex-start;
  min-width: 390px;
}

.picker {
  border: 1px solid;
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}



.picker-list {
  border: 1px solid;
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
}

.picker-list ul {
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  list-style: none;
}

.picker-list ul li {
  padding: 5px 15px;
  border-radius: 20px;
  background-color: black;
  color: white;
  margin-right: 20px;
}

.picker-map {
  border: 1px solid;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-image: url(./assets/map-ZJG.svg);
  background-size: cover;
  height: 70px;
  min-width: 90px;
}


.title {
  border: 1px solid black;
  font-weight: 700;
  font-size: 32px;
  line-height: 32px;
  display: flex;
  text-align: center;
  justify-content: start;
  align-items: center;
}

.top-bar {
  border: 1px solid;
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}

.caption {
  border: 1px solid;
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}

.container {
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

.pick {
  border: 1px solid black;
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

.position {
  display: flex;
  font-weight: 900;
  font-size: 36px;
  line-height: 36px;
  margin-bottom: 50px;
}

.icon {
  display: flex;
  font-weight: 900;
  font-size: 64px;
  line-height: 64px;
  margin-bottom: 50px;
}

.description {
  display: flex;
  font-size: 18px;
  line-height: 24px;
}

.button {
  padding: 15px 50px;
  display: flex;
  flex-direction: row;
  font-weight: 500;
  font-size: 22px;
  line-height: 28px;
  align-items: center;
  text-align: center;
  justify-content: center;
  border-radius: 82px;
  background: #000000;
  color: #FFFFFF;
  border: none;
}
</style>
