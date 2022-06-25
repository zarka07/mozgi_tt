<template>
  <router-view v-slot="{ Component }">
    <transition appear name="slide-fade" mode="out-in">
      <div :key="$route.name">
        <component :is="Component" />
      </div>
    </transition>
  </router-view>
</template>

<script>
import HomeView from "./views/HomeView.vue";
import AboutView from "./views/AboutView.vue";
export default {
  components: { HomeView, AboutView },

  computed: {
    Component() {
      return HomeView ? HomeView : AboutView;
    },
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #bebebe;
  height: 97vh;
}
div{
  height: 100%;
}
.slide-fade-enter-active {
  transition: all 1.5s;
}

.slide-fade-leave-active {
  transition: all 1.5s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from{
  transform: translateX(1200px);
  opacity: 0.3;
}
.slide-fade-leave-to {
  transform: translateX(-1200px);
  opacity: 0.3;
}

nav {
  padding: 15px;
}
</style>
