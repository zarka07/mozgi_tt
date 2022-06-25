<template>
  <header>
    <Header />
  </header>
  <main class="main">
    <aside class="main__left"><button @click="toAbout">where?</button></aside>
    <article class="main__article">
      <section id="text" class="main__article__title">FULL-CYCLE EVENT AGENCY</section>
      <section id="run" :style="styleWidth" class="main__article__runningtext">
        <div class="article__runningtext__top marquee marquee__top">
          <span>FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY</span>
        </div>
        <div class="article__runningtext__bottom marquee marquee__bottom">
          <span>FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY</span>
        </div>
      </section>
      <section class="main__article__buttons">
        <img class="rot" src="../assets/buttons.svg" alt="buttons" />
      </section>
    </article>

    <aside class="main__right"><button @click="toAbout">what?</button></aside>
    <aside class="main__bottom"><button @click="toAbout">who?</button></aside>
  </main>
</template>

<script>
import Header from "../components/Header.vue";
export default {
  name: "HomeView",
  components: {
    Header,
  },
  data(){
    return{
      styleWidth:'width:'+document.documentElement.clientWidth+'px'
    }
  },
  mounted() {
    let text = document.getElementById("text"),
      body = document.body,
      steps = 7;
    function threedee(e) {
      let x = Math.round(
          (steps / (window.innerWidth / 2)) * (window.innerWidth / 2 - e.clientX)
        ),
        y = Math.round(
          (steps / (window.innerHeight / 2)) * (window.innerHeight / 2 - e.clientY)
        ),
        shadow = "",
        color = 190,
        radius = 3,
        i,
        tx,
        ty;

      for (i = 0; i < steps; i++) {
        tx = Math.round((x / steps) * i);
        ty = Math.round((y / steps) * i);
        if (tx || ty) {
          color -= 3 * i;
          shadow +=
            tx + "px " + ty + "px 0 rgb(" + color + ", " + color + ", " + color + "), ";
        }
      }
      shadow +=
        x +
        "px " +
        y +
        "px 1px rgba(0,0,0,.2), " +
        x * 2 +
        "px " +
        y * 2 +
        "px 6px rgba(0,0,0,.3)";

      text.style.textShadow = shadow;
      text.style.webkitTransform =
        "translateZ(0) rotateX(" + y * 1.5 + "deg) rotateY(" + -x * 1.5 + "deg)";
      text.style.MozTransform =
        "translateZ(0) rotateX(" + y * 1.5 + "deg) rotateY(" + -x * 1.5 + "deg)";
    }
    document.addEventListener("mousemove", threedee, false);
  },
  methods:{
    toAbout(){
      this.$router.push({name:'about'})
    }
  }
};
</script>

<style scoped>
button {
  background: transparent;
  border:none;
  color:#FFF;
  font-family: "Grtsk Giga Semibold";
  font-size: 12px;
}
.main {
  height: 70vh;
  background-image: url("../assets/Ellipse.svg");
  background-repeat: no-repeat;
  background-position: center;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow-wrap: break-word;
  box-sizing: border-box;
}
.main__article {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 90%;
}
@font-face {
  font-family: "Grtsk Giga";
  src: local("Grtsk"), url("../assets/fonts/GrtskGiga-Bold.ttf") format("truetype");
}
.main__article__title {
  z-index: 0;
  font-weight: 700;
  font-size: 50px;
  text-align: center;
  font-family: "Grtsk Giga";
  width: 80vw;
  -webkit-tranform: translateZ(0);
  -webkit-transition-duration: 0.05s;
  -moz-tranform: translateZ(0);
  text-shadow: 0 0 1px rgba(0, 0, 0, 0.2);
}
@font-face {
  font-family: "Grtsk Giga Italic";
  src: local("Grtsk italic"),
    url("../assets/fonts/GrtskGiga-Italic.woff") format("truetype");
}
.main__article__runningtext {
  z-index: 999;
  position: absolute;
  font-family: "Grtsk Giga Italic";
  transform: rotate(-22deg);
  opacity: 0.1;
  border: 1px #373737;
  /* width: 1400px; */
}
.marquee {
  width: 100%;
  white-space: nowrap;
  overflow: hidden;
}
.marquee__top span {
  color: #212121;
  font-size: 25px;
  display: inline-block;
  padding-left: 100%;
  -webkit-animation: marquee__top 10s infinite linear;
  animation: marquee__top 10s infinite linear;
}
.marquee__bottom span {
  color: #212121;
  font-size: 25px;
  display: inline-block;
  padding-left: 100%;
  -webkit-animation: marquee__bottom 10s infinite linear;
  animation: marquee__bottom 10s infinite linear;
}

@-webkit-keyframes marquee__top {
  100% {
    -webkit-transform: translate(0, 0);
  }
  0% {
    -webkit-transform: translate(-100%, 0);
  }
}
@keyframes marquee__top {
  100% {
    transform: translate(0, 0);
  }
  0% {
    transform: translate(-100%, 0);
  }
}

@-webkit-keyframes marquee__bottom {
  0% {
    -webkit-transform: translate(0, 0);
  }
  100% {
    -webkit-transform: translate(-100%, 0);
  }
}
@keyframes marquee__bottom {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(-100%, 0);
  }
}


aside:after {
  position: absolute;
  content: "";
  width: 0;
  height: 2px;
  background-color: #fff;
  bottom: 0px;
  left: 0;
  transition: all ease-in 0.25s;
}
aside:hover:after {
  width: 100%;
  color: #fff !important;
}
@font-face {
  font-family: "Grtsk Giga Semibold";
  src: local("Grtsk semibold"), url("../assets/fonts/GrtskGiga-Semibold.woff");
}

.main__left {
  transform: rotate(-90deg);
}
.main__right {
  transform: rotate(90deg);
}
.main__bottom {
  position: absolute;
  bottom: 25px;
}
.main__article__buttons {
  position: absolute;
  top: 20vh;
  left: 52vw;
}
img.rot:hover {
  animation: 15s linear 0s normal none infinite running rot;
  -webkit-animation: 15s linear 0s normal none infinite running rot;
}
@keyframes rot {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(-360deg);
  }
}
@-webkit-keyframes rot {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
