<template>
  <nav class="nav">
    <div class="nav__group53">
      <img src="../assets/Group53.svg" alt="group53" />
      <button class="nav__lang nav__lang__ua">UA</button>
      <button class="nav__lang nav__lang__usa">EN</button>
    </div>

    <a id="nav__title" :style="style" href="#" data-content=""
      ><img src="../assets/Union.svg" alt="union"
    /></a>
    <!-- <img class="nav__union" src="../assets/Union.svg" alt="union"> -->
  </nav>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      style: "clip-path:polygon(0 100%, 100% 100%, 100% 100%, 0 100%)",
    };
  },
  mounted() {
    let text = document.getElementById("nav__title");
    setTimeout(this.set, 1000);
  },
  methods: {
    set() {
      this.style =
        "clip-path:polygon(0 0, 100% 0, 100% 100%, 0 100%); display:inline-block";
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}
*::before,
*::after {
  box-sizing: border-box;
}
@font-face {
  font-family: "Grtsk Giga";
  src: local("Grtsk"), url("../assets/fonts/GrtskGiga-Bold.ttf") format("truetype");
}
.nav {
  /* display: flex;
  align-items: center;
  justify-content: center;
  margin: 0; */
  position: relative;
  /* background-color: lightblue; */
}
.nav__group53 {
  position: absolute;
  left: 20px;
  top: 20px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  /* position: relative; */
}
.nav__lang {
  opacity: 0;
  position: absolute;
  left: 10px;
  /* transition: opacity 0.3s; */
  border: none;
  cursor: pointer;
  font-size: 10px;
  -webkit-transition: all 0.8s cubic-bezier(0.12, 0.41, 0.67, 0.95);
  transition: all 0.8s cubic-bezier(0.12, 0.41, 0.67, 0.95);
}

.nav__lang__ua {
  margin-left: 50px;
}
.nav__group53:hover .nav__lang__ua {
  opacity: 1;
  /* margin-left: 50px; */
  -webkit-transform: translate(0px);
  transform: translate(30px);
}
.nav__group53:hover .nav__lang__usa {
  opacity: 1;
  -webkit-transform: translate(0px);
  transform: translate(30px);
}

a {
  position: relative;
  display: inline-block;
  font-size: 2em;
  color: transparent;
  font-weight: 700;
  font-family: "Grtsk Giga";
  text-decoration: none;
  overflow: hidden;
  transition: clip-path 700ms ease;
}

a::before {
  position: absolute;
  content: attr(data-content);
  color: #000;
  text-decoration: none;
  transition: clip-path 700ms ease;
}
button {
  color: #fff;
  background-color: transparent;
  font-family: "Grtsk Giga";
}
</style>
