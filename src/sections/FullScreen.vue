<template>
  <section class="fullScreen">
    <!-- <img src="/src/assets/intro_img1.png" alt="" /> -->
    <div></div>
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
        end: "bottom+=30vh top",
        scrub: true,
        pin: true,
        pinSpacing: false,
      },
    });
    gsap.to(".fullScreen div", {
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

    // gsap.to(".fullScreen", {
    //   scale: 0.8,
    //   yPercent: -20,
    //   immediateRender: false,
    //   scrollTrigger: {
    //     trigger: ".culture",
    //     start: "top+=30% bottom",
    //     endTrigger: ".culture",
    //     end: "top top",
    //     scrub: true,
    //     markers: true,
    //   },
    // });
  },
};
</script>

<style scoped lang="scss">
.fullScreen {
  width: 100%;
  height: 200vh;
  position: relative;
  & div {
    width: 100%;
    height: 50%;
    --clip: 20% 40%;
    clip-path: inset(var(--clip));
    transition: clip-path 0.01s ease-in-out;
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, 0);
    background-image: url("/src/assets/fullScreen.png");
    background-position: center;
    background-size: cover;
  }
}
</style>
