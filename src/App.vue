<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="background">
    <div class="title">今天去哪学📚</div>
    <div class="picker">
      想在什么方位？
      <div class="picker-list">
        <ul>
          <li>东</li>
          <li>西</li>
          <li>南</li>
          <li>北</li>
        </ul>
      </div>
      <div class="picker-map">
        <svg width="82" height="64" viewBox="0 0 82 64" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M68.859 3.64228V7.28455L65.4423 9.88618L63.3397 13.0081L60.4487 18.4715L55.7179 20.5528L54.4038 26.0163H55.7179V23.4146L59.1346 20.5528H62.2885L64.391 23.4146L61.2372 30.1789L59.1346 30.9593L62.2885 32.7805L60.4487 40.5854V45.5285L62.2885 50.7317L64.391 51.7724L66.2308 46.3089H62.2885V39.8049H64.391V43.4472H65.4423V39.8049L67.5449 38.7642L68.3333 36.9431H66.2308L65.4423 28.3577L67.5449 24.1951L64.391 20.5528L65.4423 11.4472L71.2244 7.80488L78.3205 4.42276L82 21.5935L80.9487 45.5285V61.3984H72.2756L63.3397 63.2195L61.2372 59.5772H53.6154L54.4038 60.3577H61.2372L62.2885 64H48.8846L45.9936 55.935L44.4167 44.748L43.6282 30.9593L39.4231 3.64228L66.2308 0V3.64228H68.859Z"
            fill="#ECECEC" />
          <path
            d="M41.5256 32L36.7949 3.64228L0 22.374L1.57692 28.3577V43.4472H2.62821L3.15385 40.5854L19.4487 40.065L22.8654 37.9837L30.2244 38.7642L31.8013 35.6423L34.4295 38.7642H36.7949L38.8974 37.9837V40.065L40.7372 39.8049V44.748H42.5769L41.5256 32Z"
            fill="#ECECEC" />
          <path
            d="M44.4167 55.935L42.5769 46.3089L39.4231 45.5285H36.7949L31.8013 43.4472L28.6474 44.748L26.5449 51.7724L25.4936 61.9187L32.5897 63.2195L47.0449 64L44.4167 55.935Z"
            fill="#ECECEC" />
          <path
            d="M25.2308 52.5528L27.5962 42.1463L25.4936 41.2213V38.7642H22.8654L19.4487 41.1057H3.94231L3.15385 44.748L1.57692 45.5285L2.62821 55.935H10.5128L19.4487 60.3577L24.7051 61.3984L25.2308 52.5528Z"
            fill="#ECECEC" />
          <path
            d="M42.44 23.5147L39 4.01471L65.9467 0V4.01471H68.24V6.88235L65.3733 9.17647L60.2133 18.9265L55.6267 20.6471L53.9067 26.3824H55.6267V23.5147L59.0667 21.2206L61.9333 20.6471L63.6533 23.5147L61.36 29.8235L59.0667 30.9706L61.9333 33.2647L43.5867 37.8529V32.6912L42.44 23.5147Z"
            fill="black" />
          <path
            d="M64.8 20.0735L65.3733 12.0441L78.56 4.01471L82 21.2206L80.8533 37.8529L67.0933 39L68.24 37.2794H66.52L64.8 28.6765L67.0933 24.0882L64.8 20.0735Z"
            fill="black" />
        </svg>
      </div>
    </div>
    <div class="picker">
      想要什么氛围？
      <div class="picker-list">
        <ul>
          <li>东</li>
          <li>西</li>
          <li>南</li>
          <li>北</li>
        </ul>
      </div>
    </div>
    <div class="container">
      <div class="caption">
        <h1>今天去🚀</h1>
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
      <div class="pick">
        <div class="position">{{position}}</div>
        <div class="icon">{{icon}}</div>
        <div class="description">{{description}}</div>
        <button class="button" @click="getPosition()">开roll！</button>
      </div>
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
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: flex-start;
  min-width: 500px;
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

.container {
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

.pick {
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
