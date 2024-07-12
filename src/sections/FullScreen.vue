<template>
  <section class="fullScreen">
    <img src="/src/assets/header.webp" alt="" />
  </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
export default {
  name: "FullScreen",
  components: {},
  data() {
    return {};
  },
  mounted() {
    gsap.to(".fullScreen", {
      scrollTrigger: {
        trigger: ".fullScreen",
        start: "top top",
        end: "bottom top",
        scrub: true,
        pin: true,
      },
    });
    gsap.to(".fullScreen img", {
      "--clip": "0% 0%",
      ease: "power1.inOut",
      // yPercent: -50,
      scrollTrigger: {
        trigger: ".fullScreen",
        start: "center center",
        end: "bottom top",
        scrub: true,
      },
    });
  },
};
</script>

<style scoped lang="scss">
.fullScreen {
  width: 100%;
  height: 100%;
  position: relative;
  & img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    --clip: 20% 40%;
    clip-path: inset(var(--clip));
    transition: clip-path 0.01s ease-in-out;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
}
</style>
