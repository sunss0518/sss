<template>
  <div class="main">
    <div class="container" ref="container" :style="{height: containerWidth*0.47+'px'}">
      <video 
        id='video'
        class="videoBox"
        :src='dataSrc[videoName]'
        muted 
        autoplay 
        controls
        :width="videoWidth" 
        :height="videoWidth*0.61"
        :style="{top: containerWidth*0.07+'px', left: containerWidth*0.305+'px'}"
        type='video/mp4'
      >
      </video>
    </div>
    <div class="list-wrap"
      :style="{height: videoWidth*0.6+'px'}">
      <ul
        class="card-list"
        :style="{top: '-50px',height: videoWidth*0.6+'px'}"
      >
        <li class="card-item" :style="{margin: '0 2.5%',height: videoWidth*0.6}">
          <img src="../assets/quicklib.png" alt="">
          <h5>QuickLib</h5>
          <div class="card-btn-area">
            <span class="disabled">Website</span>
            <span @click="switchVideo('quicklib')">Video</span>
          </div>
        </li>
        <li class="card-item" :style="{margin: '0 2.5%',height: videoWidth*0.6}">
          <img src="../assets/kairoz.png" alt="">
          <h5>Kairoz</h5>
          <div class="card-btn-area">
            <span class="disabled">Website</span>
            <span @click="switchVideo('kairoz')">Video</span>
          </div>
        </li>
        <li class="card-item" :style="{margin: '0 2.5%',height: videoWidth*0.6}">
          <img src="../assets/symbolEditor.png" alt="">
          <h5>SymbolEditor</h5>
          <div class="card-btn-area">
            <span @click="goSite('symbolEditor')">Website</span>
            <span @click="switchVideo('symbolEditor')">Video</span>
          </div>
        </li>
      </ul>
    </div>
    <div class="footer">
      <img src="../assets/logo.png" alt="">
      <span>Greetings from Sun.</span>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      containerWidth: 900,
      videoWidth: 300,
      videoName: 'quicklib',
      dataSrc: {
        quicklib: "https://7373-sss-9gd5kp6057cc6d9a-1305842996.tcb.qcloud.la/videos/quicklib.mp4?sign=00b0a01538999f2b5a2073469b0d2a2e&t=1648886651",
        kairoz: "https://7373-sss-9gd5kp6057cc6d9a-1305842996.tcb.qcloud.la/videos/kairoz.mp4?sign=41b554f6ef9ecc4084ccd03e9973ea58&t=1648886439",
        symbolEditor: "https://7373-sss-9gd5kp6057cc6d9a-1305842996.tcb.qcloud.la/videos/symbolEditor.mp4?sign=a4880c9b032ce16c4fe56d69d751b30c&t=1648886539"
      }
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.containerWidth = this.$refs.container.offsetWidth;
      this.videoWidth = this.$refs.container.offsetWidth * 0.38;
    });
  },
  methods: {
    goSite(name) {
      window.open(`https://sss-9gd5kp6057cc6d9a-1305842996.tcloudbaseapp.com/${name}/`)
    },
    switchVideo(name) {
      this.videoName = name;
    }
  }
};
</script>

<style>
* {
  user-select: none;
}
.main {
  position: relative;
  margin: 0 auto;
  background-color: #efefef;
}
.container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-image: url('./assets/bg.png');
  background-size: 100% auto;
  background-repeat: no-repeat;
  background-color: #efefef;
}

.videoBox {
  position: absolute;
}
.list-wrap {
  position: relative;
  width: 100%;
  min-height: 200px; 
}
.card-list {
  position: absolute;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  padding: 10px 0 10px 5%;
  list-style: none;
}
.card-item {
  display: flex;
  flex-flow: column;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 50px;
  width: 26%;
  border-radius: 6px;
  box-shadow: 0 0 8px #aaa;
  background-color: rgba(255, 255, 255, .8);
  cursor: pointer;
}
.card-item:hover {
  box-shadow: 0 0 4px #aaa;
}
.card-item img {
  width: 100%;
  border-radius: 6px 6px 0 0;
}
.card-item h5 {
  height: 40px;
  line-height: 40px;
}
.card-btn-area {
  width: 100%;
  height: 40px;
  border-top: 1px solid #cfcfcf;
}
.card-btn-area span {
  display: inline-block;
  width: 48%;
  height: 40px;
  line-height: 40px;
  text-align: center;
  background-image: -webkit-linear-gradient(left, #129090, #de6912);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
.card-btn-area span:not(.disabled):hover {
  background-image: -webkit-linear-gradient(right, #129090, #129090);
}
.card-btn-area span:first-child {
  border-right: 1px solid #cfcfcf;
}
.card-btn-area span.disabled {
  background-image: -webkit-linear-gradient(left, #cfcfcf, #cfcfcf);
  -webkit-text-fill-color: #cfcfcf;
  cursor: not-allowed;
}

.footer {
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  bottom: -100px;
  width: 100%;
  height: 100px;
  line-height: 100px;
  text-align: center;
  background-color: #fff;
}
.footer img {
  margin-right: 20px;
}
.footer span {
  display: inline-block;
  padding-left: 20px;
  height: 30px;
  line-height: 30px;
  border-left: 1px solid #666;
}
</style>
