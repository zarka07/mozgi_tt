<template>
  <nav class="nav">
    <article class="footer__article">
      Who?
    </article>
  </nav>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
@font-face {
  font-family: "Grtsk Giga Semibold";
  src: local("Grtsk semibold"),
    url("../assets/fonts/GrtskGiga-Semibold.ttf") format("truetype");
}
article {
  text-align: center;
  font-family: "Grtsk Giga Semibold";
  color:#FFF;
  font-size: 12px;
}
article{
  text-decoration: none;
}
article:after {
  position: absolute;
  content: "";
  width: 0;
  height: 3px;
  background-color: #42b983;
  bottom: 0px;
  left: 0;
  transition: all ease-in 0.25s;
}

article:hover:after {
  width: 100%;
  color:#FFF!important;
}


</style>
