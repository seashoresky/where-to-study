<template>
  <div class="background">
    <div class="top-bar">
      <div class="title">今天去哪学📚</div>
    </div>
    <div class="picker">
      <div class = "picker-container">
        <div class = "text">想在什么方位</div>
        <div class="picker-list">
          <div v-for="(azimuth, index) in azimuths" :key="azimuth.text" :class = "azimuth.class" @click="chooseAzimuth(index)">
            {{azimuth.text}}
          </div>
        </div>
      </div>
      <div class="picker-map">
        <svg v-show="map == 0" width="82" height="64" viewBox="0 0 82 64" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M68.859 3.64228V7.28455L65.4423 9.88618L63.3397 13.0081L60.4487 18.4715L55.7179 20.5528L54.4038 26.0163H55.7179V23.4146L59.1346 20.5528H62.2885L64.391 23.4146L61.2372 30.1789L59.1346 30.9593L62.2885 32.7805L60.4487 40.5854V45.5285L62.2885 50.7317L64.391 51.7724L66.2308 46.3089H62.2885V39.8049H64.391V43.4472H65.4423V39.8049L67.5449 38.7642L68.3333 36.9431H66.2308L65.4423 28.3577L67.5449 24.1951L64.391 20.5528L65.4423 11.4472L71.2244 7.80488L78.3205 4.42276L82 21.5935L80.9487 45.5285V61.3984H72.2756L63.3397 63.2195L61.2372 59.5772H53.6154L54.4038 60.3577H61.2372L62.2885 64H48.8846L45.9936 55.935L44.4167 44.748L43.6282 30.9593L39.4231 3.64228L66.2308 0V3.64228H68.859Z" fill="#ECECEC"/>
          <path d="M41.5256 32L36.7949 3.64228L0 22.374L1.57692 28.3577V43.4472H2.62821L3.15385 40.5854L19.4487 40.065L22.8654 37.9837L30.2244 38.7642L31.8013 35.6423L34.4295 38.7642H36.7949L38.8974 37.9837V40.065L40.7372 39.8049V44.748H42.5769L41.5256 32Z" fill="#ECECEC"/>
          <path d="M44.4167 55.935L42.5769 46.3089L39.4231 45.5285H36.7949L31.8013 43.4472L28.6474 44.748L26.5449 51.7724L25.4936 61.9187L32.5897 63.2195L47.0449 64L44.4167 55.935Z" fill="#ECECEC"/>
          <path d="M25.2308 52.5528L27.5962 42.1463L25.4936 41.2213V38.7642H22.8654L19.4487 41.1057H3.94231L3.15385 44.748L1.57692 45.5285L2.62821 55.935H10.5128L19.4487 60.3577L24.7051 61.3984L25.2308 52.5528Z" fill="#ECECEC"/>
          <path d="M42.44 23.5147L39 4.01471L65.9467 0V4.01471H68.24V6.88235L65.3733 9.17647L60.2133 18.9265L55.6267 20.6471L53.9067 26.3824H55.6267V23.5147L59.0667 21.2206L61.9333 20.6471L63.6533 23.5147L61.36 29.8235L59.0667 30.9706L61.9333 33.2647L43.5867 37.8529V32.6912L42.44 23.5147Z" fill="black"/>
          <path d="M64.8 20.0735L65.3733 12.0441L78.56 4.01471L82 21.2206L80.8533 37.8529L67.0933 39L68.24 37.2794H66.52L64.8 28.6765L67.0933 24.0882L64.8 20.0735Z" fill="black"/>
        </svg>
        <svg v-show="map == 1" width="82" height="65" viewBox="0 0 82 65" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M68.859 3.64228V7.28455L65.4423 9.88618L63.3397 13.0081L60.4487 18.4715L55.7179 20.5528L54.4038 26.0163H55.7179V23.4146L59.1346 20.5528H62.2885L64.391 23.4146L61.2372 30.1789L59.1346 30.9593L62.2885 32.7805L60.4487 40.5854V45.5285L62.2885 50.7317L64.391 51.7724L66.2308 46.3089H62.2885V39.8049H64.391V43.4472H65.4423V39.8049L67.5449 38.7642L68.3333 36.9431H66.2308L65.4423 28.3577L67.5449 24.1951L64.391 20.5528L65.4423 11.4472L71.2244 7.80488L78.3205 4.42276L82 21.5935L80.9487 45.5285V61.3984H72.2756L63.3397 63.2195L61.2372 59.5772H53.6154L54.4038 60.3577H61.2372L62.2885 64H48.8846L45.9936 55.935L44.4167 44.748L43.6282 30.9593L39.4231 3.64228L66.2308 0V3.64228H68.859Z" fill="#ECECEC"/>
          <path d="M41.5256 32L36.7949 3.64228L0 22.374L1.57692 28.3577V43.4472H2.62821L3.15385 40.5854L19.4487 40.065L22.8654 37.9837L30.2244 38.7642L31.8013 35.6423L34.4295 38.7642H36.7949L38.8974 37.9837V40.065L40.7372 39.8049V44.748H42.5769L41.5256 32Z" fill="#ECECEC"/>
          <path d="M44.4167 55.935L42.5769 46.3089L39.4231 45.5285H36.7949L31.8013 43.4472L28.6474 44.748L26.5449 51.7724L25.4936 61.9187L32.5897 63.2195L47.0449 64L44.4167 55.935Z" fill="#ECECEC"/>
          <path d="M25.2308 52.5528L27.5962 42.1463L25.4936 41.2213V38.7642H22.8654L19.4487 41.1057H3.94231L3.15385 44.748L1.57692 45.5285L2.62821 55.935H10.5128L19.4487 60.3577L24.7051 61.3984L25.2308 52.5528Z" fill="#ECECEC"/>
          <path d="M44 56L42.5 46H36.5L32.5 43L29 44.5L27 51L25.5 61.5L31 63L47.5 64.5L44 56Z" fill="black"/>
          <path d="M25 53L27.5 42H25.5V39H23L20 41H4L3 44.5L1.5 46L2.5 56H11L18 59.5L24 61.5L25 53Z" fill="black"/>
        </svg>
        <svg v-show="map == 2" width="82" height="64" viewBox="0 0 82 64" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M68.859 3.64228V7.28455L65.4423 9.88618L63.3397 13.0081L60.4487 18.4715L55.7179 20.5528L54.4038 26.0163H55.7179V23.4146L59.1346 20.5528H62.2885L64.391 23.4146L61.2372 30.1789L59.1346 30.9593L62.2885 32.7805L60.4487 40.5854V45.5285L62.2885 50.7317L64.391 51.7724L66.2308 46.3089H62.2885V39.8049H64.391V43.4472H65.4423V39.8049L67.5449 38.7642L68.3333 36.9431H66.2308L65.4423 28.3577L67.5449 24.1951L64.391 20.5528L65.4423 11.4472L71.2244 7.80488L78.3205 4.42276L82 21.5935L80.9487 45.5285V61.3984H72.2756L63.3397 63.2195L61.2372 59.5772H53.6154L54.4038 60.3577H61.2372L62.2885 64H48.8846L45.9936 55.935L44.4167 44.748L43.6282 30.9593L39.4231 3.64228L66.2308 0V3.64228H68.859Z" fill="#ECECEC"/>
          <path d="M41.5256 32L36.7949 3.64228L0 22.374L1.57692 28.3577V43.4472H2.62821L3.15385 40.5854L19.4487 40.065L22.8654 37.9837L30.2244 38.7642L31.8013 35.6423L34.4295 38.7642H36.7949L38.8974 37.9837V40.065L40.7372 39.8049V44.748H42.5769L41.5256 32Z" fill="#ECECEC"/>
          <path d="M44.4167 55.935L42.5769 46.3089L39.4231 45.5285H36.7949L31.8013 43.4472L28.6474 44.748L26.5449 51.7724L25.4936 61.9187L32.5897 63.2195L47.0449 64L44.4167 55.935Z" fill="#ECECEC"/>
          <path d="M25.2308 52.5528L27.5962 42.1463L25.4936 41.2213V38.7642H22.8654L19.4487 41.1057H3.94231L3.15385 44.748L1.57692 45.5285L2.62821 55.935H10.5128L19.4487 60.3577L24.7051 61.3984L25.2308 52.5528Z" fill="#ECECEC"/>
          <path d="M46 56.5L43.5 38L62 33.5L60.5 40L60 45L62.5 50.5L64 51.5L66 46.5L62.5 46L62 40H64.5V43.5H65.5V39.5L67.5 39L81 38V61.5H72.5L63.5 63L61.5 59.5H53.5L54.5 60.5H61L62 64H49L46 56.5Z" fill="black"/>
        </svg>
        <svg v-show="map == 3" width="82" height="64" viewBox="0 0 82 64" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M68.859 3.64228V7.28455L65.4423 9.88618L63.3397 13.0081L60.4487 18.4715L55.7179 20.5528L54.4038 26.0163H55.7179V23.4146L59.1346 20.5528H62.2885L64.391 23.4146L61.2372 30.1789L59.1346 30.9593L62.2885 32.7805L60.4487 40.5854V45.5285L62.2885 50.7317L64.391 51.7724L66.2308 46.3089H62.2885V39.8049H64.391V43.4472H65.4423V39.8049L67.5449 38.7642L68.3333 36.9431H66.2308L65.4423 28.3577L67.5449 24.1951L64.391 20.5528L65.4423 11.4472L71.2244 7.80488L78.3205 4.42276L82 21.5935L80.9487 45.5285V61.3984H72.2756L63.3397 63.2195L61.2372 59.5772H53.6154L54.4038 60.3577H61.2372L62.2885 64H48.8846L45.9936 55.935L44.4167 44.748L43.6282 30.9593L39.4231 3.64228L66.2308 0V3.64228H68.859Z" fill="#ECECEC"/>
          <path d="M41.5256 32L36.7949 3.64228L0 22.374L1.57692 28.3577V43.4472H2.62821L3.15385 40.5854L19.4487 40.065L22.8654 37.9837L30.2244 38.7642L31.8013 35.6423L34.4295 38.7642H36.7949L38.8974 37.9837V40.065L40.7372 39.8049V44.748H42.5769L41.5256 32Z" fill="#ECECEC"/>
          <path d="M44.4167 55.935L42.5769 46.3089L39.4231 45.5285H36.7949L31.8013 43.4472L28.6474 44.748L26.5449 51.7724L25.4936 61.9187L32.5897 63.2195L47.0449 64L44.4167 55.935Z" fill="#ECECEC"/>
          <path d="M25.2308 52.5528L27.5962 42.1463L25.4936 41.2213V38.7642H22.8654L19.4487 41.1057H3.94231L3.15385 44.748L1.57692 45.5285L2.62821 55.935H10.5128L19.4487 60.3577L24.7051 61.3984L25.2308 52.5528Z" fill="#ECECEC"/>
          <path d="M42.5 44.5H41V40H39V38L37 39L34.5 38.5L32 35.5L30 38.5L23 38L19.5 40L3.5 40.5L2.5 43.5H1.5L2 28.5L0 22.5L37 3.5L41.5 32L42.5 44.5Z" fill="black"/>
        </svg>
      </div>
    </div>
    <div class="picker-container">
      <div class = "text">想要什么氛围</div>
      <div class="picker-list">
        <div v-for="(atmosphere, index) in atmospheres" :key="atmosphere.text" :class = "atmosphere.class" @click="chooseAtmosphere(index)">
            {{atmosphere.text}}
          </div>
      </div>
    </div>
    <div class="container">
      <div class="caption">今天去🚀</div>
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
            icon: "❓",
            positions: ["东教", "西教", "北教", "启真湖底", "管院楼顶", "小剧场b217"],
            icons: ["🏫", "💑", "🧑‍🎓", "🤿", "🏢", "🎭"],
            descriptions: ["经典永不过时", "幸运的人不会遇到情侣", "误入老狗们的世界", "咕噜咕噜", "一跃解……", "凭此截图获取一天潮人体验券"],
            azimuths: [
                { text: "东", class: "picker-on"},
                { text: "西", class: "picker-off"},
                { text: "南", class: "picker-off"},
                { text: "北", class: "picker-off"}
            ],
            atmospheres: [
              { text: "幽静偏僻", class: "picker-on" },
              { text: "烟火气息", class: "picker-off" },
              { text: "卷王密集", class: "picker-off" },
              { text: "另辟蹊径", class: "picker-off" },
            ],
            map: 0,
            atom: 0,
        };
    },
    methods: {
        getPosition() {
          const total = this.positions.length;
          let i = Math.floor(Math.random() * total);
          this.position = this.positions[i];
          this.description = this.descriptions[i];
          this.icon = this.icons[i];
        },
        chooseAzimuth(index){
          for(let i = 0; i < 4; i++) this.azimuths[i].class = "picker-off";
          this.azimuths[index].class = "picker-on";
          this.map = index;
        },
        chooseAtmosphere(index){
          for(let i = 0; i < 4; i++) this.atmospheres[i].class = "picker-off";
          this.atmospheres[index].class = "picker-on";
          this.atom = index;
        }
    },
}
</script>

<style scoped>
* {
  font-family: "Noto Sans SC";
}
.background {
  position: relative;
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: flex-start;
  
  background-color: #f5f5f5;
  padding: 20px;
  height: 100%;
}
.top-bar {
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
  margin-top: 20px;
  margin-bottom: 30px;
}
.title {
  font-weight: 700;
  font-size: 32px;
  line-height: 32px;
  display: flex;
}
.picker {
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}
.text{
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 23px;
  color: #000000;
  order: 0;
  flex-grow: 0;
  display: flex;
  justify-content: flex-start;
  padding-bottom: 5px;
}
.picker-container{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
.picker-list {
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: space-between;
  align-items: flex-start;
  flex-flow: wrap;
}
.picker-on{
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 5px 15px;
  background: #48B23E;
  border-radius: 20px;
  flex: none;
  order: 0;
  flex-grow: 0;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 23px;
  color: #FFFFFF;
  margin-right: 10px;
  margin-bottom: 10px;
}
.picker-off{
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 5px 15px;
  background: #FCFCFC;
  border-radius: 20px;
  flex: none;
  order: 0;
  flex-grow: 0;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 23px;
  color: #C5C5C5;
  margin-right: 10px;
  margin-bottom: 10px;
}
.picker-map {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background-size: cover;
  height: 70px;
  min-width: 90px;
}
.caption {
  display: flex;
  flex-direction: row;
  text-align: center;
  justify-content: center;
  align-items: flex-start;
  width: 100%;
  font-style: normal;
  font-weight: 700;
  font-size: 20px;
  line-height: 29px;
  color: #000000;
  flex: none;
  order: 0;
  flex-grow: 0;
  margin-top: 20px;
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
  border-radius: 6px;
  box-shadow: 0px 3px 5px 0px rgba(0, 0, 0, 0.05);
  background-color: #FFFFFF;
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  padding: 20px;
  margin-top: 20px;
  margin-bottom: 20px;
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
