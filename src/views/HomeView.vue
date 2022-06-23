<template>
  <header>
    <Header />
  </header>
  <main class="main">
    <aside class="main__left">where?</aside>
    <article class="main__article">
      <section id="text" class="main__article--title">FULL-CYCLE EVENT AGENCY</section>
      <section class="main__article--buttons">
        <img class="rot" src="../assets/buttons.svg" alt="buttons" />
      </section>
    </article>

    <aside class="main__right">what?</aside>
    <aside class="main__bottom">who?</aside>
  </main>
</template>

<script>
import Header from "../components/Header.vue";
export default {
  name: "HomeView",
  components: {
    Header,
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
};
</script>

<style scoped>
nav {
}
.main {
  height: 70vh;
  background-image: url("../assets/Ellipse.svg");
  background-repeat: no-repeat;
  background-position: center;
  display: flex;
  align-items: center;
  justify-content: center;
}
.main__article {
  display: flex;
  align-items: center;
  justify-content: center;
}
@font-face {
  font-family: "Grtsk Giga";
  src: local("Grtsk"), url("../assets/fonts/GrtskGiga-Bold.ttf") format("truetype");
}
.main__article--title {
  font-weight: 700;
  font-size: 50px;
  text-align: center;
  font-family: "Grtsk Giga";
  width: 60%;
  -webkit-tranform: translateZ(0);
  -webkit-transition-duration: 0.05s;
  -moz-tranform: translateZ(0);
  text-shadow: 0 0 1px rgba(0, 0, 0, 0.2);
}
aside {
  color: #fff;
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
aside {
  font-family: "Grtsk Giga Semibold";
  font-size: 12px;
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
.main__article--buttons {
  position: absolute;
  top: 65%;
  left: 55%;
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
