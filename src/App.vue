<template>
  <NavBar />
  <div id="smooth-wrapper">
    <div id="smooth-content">
      <Home />
      <Footer />
    </div>
  </div>
</template>

<script>
import Home from "./pages/Home.vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";

import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import ScrollSmoother from "gsap/ScrollSmoother";

gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

export default {
  name: "App",
  components: {
    Home,
    NavBar,
    Footer,
  },
  data() {
    return {};
  },
  mounted() {
    ScrollSmoother.create({
      smooth: 1, // how long (in seconds) it takes to "catch up" to the native scroll position
      effects: true, // looks for data-speed and data-lag attributes on elements
      smoothTouch: 0.1, // much shorter smoothing time on touch devices (default is NO smoothing on touch devices)
    });
  },
};
</script>

<style scoped></style>
