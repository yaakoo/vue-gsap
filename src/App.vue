<template>
  <div id="nav">
    <Header />
    <Banner />
    <Panels />
    <Logo_CSS />
    <Logo_GSAP />
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Banner from "./components/Banner.vue"
import Panels from "./components/Panels.vue"
import Logo_CSS from "./components/Logo_CSS.vue"
import Logo_GSAP from "./components/Logo_GSAP.vue"


export default {
    name: "App",
    components: {
        Header,
        Banner,
        Panels,
        Logo_CSS,
        Logo_GSAP
    }
}
</script>

<style>
body {
  background-color: #F5F5F5;
  font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
  margin: 0px;
}

a {
  text-decoration: none;
}
</style>