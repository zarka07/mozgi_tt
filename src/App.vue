<template>
  <router-view v-slot="{ Component }">
    <transition name="slide-fade" mode="out-in" >
      <div class="slide-fade__component" :key="$route.name">
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
  @import "./assets/css/App.vue.style.css";
</style>
