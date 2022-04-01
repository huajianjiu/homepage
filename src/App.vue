<template>
  <div id="app">
    <!-- Home -->
    <home></home>
    <!-- 导航条 -->
    <menu-header></menu-header>
    <!-- 关于我 -->
    <about-me></about-me>
    <!-- 项目 -->
    <project></project>
    <!-- Research -->
    <research></research>
    <!-- Publication -->
    <publication></publication>
    <!--Footer-->
    <footers></footers>
  </div>
</template>

<script>
import Footers from "./components/Footer.vue"
import Home from './components/Home.vue'
import MenuHeader from './components/MenuHeader.vue'
import AboutMe from './components/AboutMe.vue'
import Project from './components/Project.vue'
import Publication from './components/Publication.vue'
import Research from './components/Research.vue'

export default {
  name: 'App',
  components: {
    MenuHeader,
    Footers,
    Home,
    AboutMe,
    Project,
    Research,
    Publication
  }
}
</script>

<style>

</style>
