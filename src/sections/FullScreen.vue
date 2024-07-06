<template>
  <section class="fullScreen"></section>
</template>

<script>
import gsap from "gsap";
import jsonData from "../data/data.json";

export default {
  name: "FullScreen",
  components: {},
  data() {
    return {};
  },
  mounted() {
    // Ici, vous pouvez utiliser GSAP pour des animations si nécessaire
  },
};
</script>

<style scoped lang="scss">
.fullScreen {
  width: 100%;
  height: 100svh;
  background-image: url("/src/assets/header.webp");
  background-size: cover;
  background-position: center;
}
</style>
