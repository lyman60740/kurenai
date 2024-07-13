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
        pinSpacing: false,
      },
    });
    gsap.to(".fullScreen img", {
      "--clip": "0% 0%",
      ease: "power1.inOut",
      // yPercent: -50,
      scrollTrigger: {
        trigger: ".fullScreen",
        start: "top center",
        end: "center top",
        scrub: true,
      },
    });

    gsap.to(".fullScreen", {
      scale: 0.8,
      immediateRender: false,
      scrollTrigger: {
        trigger: ".fullScreen",
        start: "bottom top",
        endTrigger: ".culture",
        end: "top top",
        scrub: true,
      },
    });
  },
};
</script>

<style scoped lang="scss">
.fullScreen {
  width: 100%;
  height: 200vh;
  position: relative;
  & img {
    width: 100%;
    height: 50%;
    object-fit: cover;
    --clip: 20% 40%;
    clip-path: inset(var(--clip));
    transition: clip-path 0.01s ease-in-out;
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, 0);
  }
}
</style>
