<template>
  <div v-show="hintFlag" class = "big-background" @click="hideHint">
    <div class = "big-hint">
      <div class = "big-title">本程序纯粹随机产生</div>
      <div class = "big-info">西、南、北区开发中……</div>
      <div class = "big-info">如有其他地点未收录</div>
      <div class = "big-info">欢迎留言 求是潮公众号 后台</div>
    </div>
  </div>
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
      <div class = "hint" @click="showHint">
        <svg width="30" height="30" viewBox="0 0 30 30" fill="none" xmlns="http://www.w3.org/2000/svg">
          <g clip-path="url(#clip0_14_105)">
            <path d="M15 2.5C8.1 2.5 2.5 8.1 2.5 15C2.5 21.9 8.1 27.5 15 27.5C21.9 27.5 27.5 21.9 27.5 15C27.5 8.1 21.9 2.5 15 2.5ZM16.25 23.75H13.75V21.25H16.25V23.75ZM18.8375 14.0625L17.7125 15.2125C16.8125 16.125 16.25 16.875 16.25 18.75H13.75V18.125C13.75 16.75 14.3125 15.5 15.2125 14.5875L16.7625 13.0125C17.225 12.5625 17.5 11.9375 17.5 11.25C17.5 9.875 16.375 8.75 15 8.75C13.625 8.75 12.5 9.875 12.5 11.25H10C10 8.4875 12.2375 6.25 15 6.25C17.7625 6.25 20 8.4875 20 11.25C20 12.35 19.55 13.35 18.8375 14.0625Z" fill="black"/>
          </g>
          <defs>
            <clipPath id="clip0_14_105">
              <rect width="30" height="30" fill="white"/>
            </clipPath>
          </defs>
        </svg>
      </div>
      <div class="caption">今天去🚀</div>
      <div class="pick">
        <div class="position">{{position}}</div>
        <div class="icon">{{icon}}</div>
        <div class="description">{{description}}</div>
      </div>
      <button v-show="!rollFlag" class="button-on" @click="getPosition()">开roll</button>
      <button v-show="rollFlag" class="button-off" @click="stopGetPosition()">停停停</button>
    </div>
    <div class = "power">Powered by 求是潮 2022</div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            position: "没想法",
            description: "来，试试看",
            icon: "❓",
            positionsEast: [
              [
                {position: "启真湖畔", icon: "🚶🏻", description: "边走边学，强身健体"},
                {position: "寝室", icon: "👨‍👨‍👦‍👦", description: "也许偏僻，有时幽静"},
                {position: "安中大楼", icon: "🏙", description: "许多小组作业的诞生地"},
                {position: "机房", icon: "🖥", description: "cout<<“今天来这学”"},
              ],
              [
                {position: "教超", icon: "🧊", description: "来点冰可乐"},
                {position: "瑞幸", icon: "☕️", description: "来点冰咖啡"},
                {position: "全家", icon: "🍙", description: "来点热饭团"},
                {position: "毕至居", icon: "🍲", description: "要在这里学？红豆泥"},
                {position: "大草坪", icon: "🌿", description: "小孩：有；蚊子：多"},
                {position: "小剧场讨论区", icon: "💡", description: "旁听例会的不二之选"},
                {position: "东二麦斯威", icon: "🥣", description: "葱油面香香"},
              ],
              [
                {position: "东教教室", icon: "🏫", description: "经典永不过时"},
                {position: "东教长廊", icon: "🎵", description: "能读出声，太好了"},
                {position: "西教教室", icon: "💑", description: "幸运的人不会遇到情侣"},
                {position: "西教自习区", icon: "✏️", description: "累了还能看看墙上的字"},
                {position: "基图", icon: "📖", description: "记得预约"},
              ],
              [
                {position: "风雨操场", icon: "🏐", description: "顺便打个卡（啊？"},
                {position: "西操", icon: "⚽️", description: "小心足球"},
                {position: "东操", icon: "🏃🏻‍♀️", description: "12min跑还有多久？"},
                {position: "大食堂", icon: "🍱", description: "您吃了吗"},
                {position: "菜鸟驿站", icon: "📦", description: "拿到新书太兴奋"},
                {position: "管院楼顶", icon: "🏢", description: "一跃解……"},
                {position: "启真湖底", icon: "🤿", description: "咕噜咕噜"},
                {position: "小剧场b217", icon: "🎬", description: "凭此截图获取一天潮人体验券"},
              ]
            ],
            azimuths: [
                { text: "东", class: "picker-on"},
                { text: "西", class: "picker-disabled"},
                { text: "南", class: "picker-disabled"},
                { text: "北", class: "picker-disabled"}
            ],
            atmospheres: [
              { text: "幽静偏僻", class: "picker-on" },
              { text: "烟火气息", class: "picker-off" },
              { text: "卷王密集", class: "picker-off" },
              { text: "另辟蹊径", class: "picker-off" },
            ],
            map: 0,
            selectedAtmo: [0],
            hintFlag: false,
            time: null,
            rollFlag: false,
        };
    },
    methods: {
        getPosition() {
          this.rollFlag = true;
          const total = this.positionsEast[this.atmo].length;
          this.time = setInterval(() => {
            let i = Math.floor(Math.random() * total);
            this.position = this.positionsEast[this.atmo][i].position;
            this.description = this.positionsEast[this.atmo][i].description;
            this.icon = this.positionsEast[this.atmo][i].icon;
          }, 50)
        },
        stopGetPosition(){
          clearInterval(this.time);
          this.rollFlag = false;
        },
        chooseAzimuth(index){
          return;
          for(let i = 0; i < 4; i++) this.azimuths[i].class = "picker-off";
          this.azimuths[index].class = "picker-on";
          this.map = index;
        },
        chooseAtmosphere(index){
          // 首先判断当前点击的按钮是否已经在被选中的atmo之中
          if(this.selectedAtmo.includes(index)) {
            // 如果已经被选中，就把它从选中的atmo之中删去
            this.selectedAtmo = this.selectedAtmo.filter(item => {
              return item != index
            })
          } else {
            // 如果当前点击的按钮尚未在被选中的atmo之中，就把它加进被选中的列表
            this.selectedAtmo.push(index)
          }
          // console.log(this.selectedAtmo)
          // 遍历序号，选中的picker-on, 未选中的设为picker-off
          for(let i = 0; i < 4; i++) {
            if(this.selectedAtmo.includes(i)) {
                this.atmospheres[i].class = "picker-on"
            } else {
              this.atmospheres[i].class = "picker-off"
            }
          }
        },
        showHint(){
          this.hintFlag = true;
        },
        hideHint(){
          this.hintFlag = false;
        }
    },
}
</script>

<style scoped>
* {
  font-family: "Noto Sans SC";
}
.big-background{
  position: absolute;
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.25);
  padding: 20px;
  height: 100%;
  width: 100%;
  z-index: 100;
}
.big-hint{
  background-color: #ffffff;
	box-shadow: 0px 0px 50px rgba(43, 48, 139, 0.05);
  border-radius: 20px;
  padding: 50px;
}
.big-title{
	font-weight: 500;
	font-size: 22px;
	line-height: 24px;
	margin-bottom: 30px;
	display: flex;
	text-align: center;
	justify-content: center;
	align-items: center;
	margin-bottom: 50px;
}
.big-info{
	display: flex;
	flex-direction: row;
	font-weight: 500;
	font-size: 13px;
	line-height: 24px;
	color: #545464;
	margin-top: 10upx;
  text-align: center;
	justify-content: center;
	align-items: center;
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
  justify-content: flex-start;
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
.picker-disabled{
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 5px 15px;
  background: #f5f5f5;
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
.hint{
  position: absolute;
  right: 20px;
  bottom: 475px;
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
.button-on {
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
.button-off {
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
  background: #ffffff;
  color: #000000;
  border: none;
}
.power{
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
  font-style: normal;
  font-weight: 500;
  font-size: 12px;
  line-height: 17px;
  color: #C0C0C0;
  margin-top: 20px;
  width: 100%;
}
</style>
