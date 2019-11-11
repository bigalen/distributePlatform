
    <template>
  <div id="home">
    <router-view></router-view>
    <div class="blank"></div>
    <div class="logo"></div>
    <div class="appname">爱上记录</div>
    <div class="appname"
         style="font-size:12px">记录我的成长</div>
    <div class="downloadbtn">
      <button @click="download">下载并安装</button>
    </div>
    <div class="info">
      1. APP内含<span>目标打卡、消费记录、日记、学习笔记、快捷访问以及许多小工具</span><br />
      <hr>
      2. 目标打卡：含每日目标、每月目标、半年目标
      <hr>
      3. 消费记录：记录您的每一笔消费，并为您做好统计
      <hr>
      4. 日记：很方便的记录每一天
      <hr>
      5. APP端与Web端( <a style="color:blue"
         target="_blank"
         href="http://www.pernode.com">www.pernode.com</a> )数据互通
      <hr>
      6. web端更适合规划次日，以及做学习笔记
      <hr>
      7. 更多的功能仍在规划中,很期待您参与进来一起改善APP
    </div>
    <div class="blank"></div>
    <div class="tip-layer" v-if="showTip">
        <h3>请点击右上角 ... </h3>
        <h3>选择在浏览器中打开</h3>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      showTip:false
    }
  },
  methods: {
    download () {
      var src = 'https://distributeplateform.oss-cn-beijing.aliyuncs.com/爱上记录.apk';
      var form = document.createElement('form');
      form.action = src;
      document.getElementsByTagName('body')[0].appendChild(form);
      form.submit();
    }
  },
  created () {
    const ua = navigator.userAgent.toLowerCase()
    const testUa = regexp => regexp.test(ua)
    if (testUa(/micromessenger/ig) || testUa(/qqbrowser/ig)) {
      this.showTip = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#home {
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  background-image: url("../../public/bg.png");
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}
.blank {
  flex: 1;
}
.logo {
  flex: 0 0 64px;
  width: 64px;
  height: 64px;
  border-radius: 8px;
  background-image: url("../../public/favicon.png");
  background-size: cover;
  background-position: center;
}
.appname {
  flex: 0 0 30px;
  width: 100%;
  color: #fff;
  line-height: 30px;
}
.downloadbtn {
  flex: 0 0 40px;
  width: 100%;
  margin-top: 20px;
}
.downloadbtn button {
  width: 96px;
  height: 30px;
  padding: 0;
  margin: 0;
  border: none;
  background: #ffaa18;
  border-radius: 20px;
}
a {
  color: #fff;
}
.info {
  flex: 1;
  width: 80%;
  color: #333;
  text-align: left;
  background: rgba(255, 255, 255, 0.7);
  font-size: 12px;
  padding: 10px;
  border-radius: 10px;
}
.tip-layer{
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center
}
.tip-layer h3{
  color: #fff;
  margin-bottom: 60px
}
</style>
