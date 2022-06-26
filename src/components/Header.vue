<template>
  <nav class="nav">
    <div class="nav__group53">
      <img src="../assets/Group53.svg" alt="group53" />
      <button class="nav__lang nav__lang__ua">UA</button>
      <button class="nav__lang nav__lang__usa">EN</button>
    </div>

    <a id="nav__title" :style="style"><img src="../assets/Union.svg" alt="union" /></a>
    
    <button class="nav__group176" @click="showDropdown = !showDropdown">
      <img src="../assets/Group176.svg" alt="two lines" />
      <ul class="dropdown" v-if="showDropdown">
        <li><button @click="toAbout" class="dropDownButton">where?</button></li>
        <li><button @click="toAbout" class="dropDownButton">what?</button></li>
        <li><button @click="toAbout" class="dropDownButton">who?</button></li>
      </ul>
    </button>
  </nav>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      showDropdown: false,
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
    toAbout() {
      this.$router.push({ name: "about" });
    },
  },
};
</script>

<style scoped>
@font-face {
  font-family: "Grtsk Giga";
  src: local("Grtsk"), url("../assets/fonts/GrtskGiga-Bold.ttf") format("truetype");
}

.nav {
  position: relative;
}

.nav__group53 {
  position: absolute;
  left: 20px;
  top: 20px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}

.nav__group176 {
  position: absolute;
  right: 20px;
  top: 25px;
  width: 100px;
  height: auto;
  text-align: right;
  visibility: hidden;
  padding: 0;
}

.dropdown {
  list-style-type: none;
  padding: 0;
}

button.dropDownButton {
  margin-bottom: 5px;
  background: transparent;
  border: none;
  color: #000;
  font-family: "Grtsk Giga Semibold";
  font-size: 12px;
}

button.dropDownButton:hover {
  color: #fff;
}

.nav__lang {
  opacity: 0;
  position: absolute;
  border: none;
  cursor: pointer;
  font-size: 10px;
  -webkit-transition: all 0.8s cubic-bezier(0.12, 0.41, 0.67, 0.95);
  transition: all 0.8s cubic-bezier(0.12, 0.41, 0.67, 0.95);
}

.nav__lang__usa {
  left: 20px;
}

.nav__lang__ua {
  left: 50px;
}

.nav__group53:hover .nav__lang__ua {
  opacity: 1;
  -webkit-transform: translate(30px);
  transform: translate(30px);
  transition: all 1s cubic-bezier(0.12, 0.41, 0.67, 0.95);
}

.nav__group53:hover .nav__lang__usa {
  opacity: 1;
  -webkit-transform: translate(30px);
  transform: translate(30px);
  transition: all 1s cubic-bezier(0.12, 0.41, 0.67, 0.95);
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

@media (max-width: 480px) {
  .nav__group176 {
    visibility: visible;
    z-index: 999;
  }
}
</style>
