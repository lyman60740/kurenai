<template>
  <nav>
    <div class="lvl_nav">
      <div class="logo">
        <svg
          width="63"
          height="48"
          viewBox="0 0 63 48"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M25.9703 4.48583L4.91768 44L4 43.5142L25.0526 4L25.9703 4.48583Z"
            fill="#FFF8E8"
          />
          <path
            d="M45.2156 14.3374H58.2521V15.5789H45.2156V14.3374ZM44.0011 33.5816H58.6569V34.8502H44.0011V33.5816ZM50.9106 14.6883H52.2332V34.2564H50.9106V14.6883ZM39.5746 23.5682H40.8432V35.8758H39.5746V23.5682ZM39.1158 11.3414L40.3573 11.8812C39.2507 13.7436 37.7392 16.0648 36.5517 17.4683L35.58 17.0094C36.7676 15.552 38.306 13.0688 39.1158 11.3414ZM42.6245 14.2294L43.8661 14.8232C41.8958 17.8192 39.0348 21.6518 36.7676 24L35.8499 23.4602C38.0631 21.085 40.9511 17.0904 42.6245 14.2294ZM34.1495 16.3077L34.8782 15.498C36.5787 16.8475 38.549 18.7099 39.4397 19.9784L38.7379 20.9501C37.7662 19.6545 35.8499 17.6572 34.1495 16.3077ZM42.0038 20.2753L43.0024 19.7355C44.4329 21.4359 45.9714 23.7571 46.6191 25.2416L45.5665 25.8623C44.9457 24.3509 43.4342 21.9757 42.0038 20.2753ZM34.0685 23.2982C36.7406 23.1903 40.7892 23.0013 44.8648 22.7854L44.8378 23.973C40.9511 24.1889 37.0105 24.4318 34.2035 24.5938L34.0685 23.2982ZM42.8135 26.726L43.8931 26.3752C44.8378 28.0486 45.7284 30.3158 46.0523 31.7463L44.8917 32.1781C44.5679 30.6937 43.7042 28.4265 42.8135 26.726ZM36.1738 26.5371L37.4693 26.753C36.9835 29.3171 36.2008 31.9082 35.2291 33.6356C34.9592 33.4737 34.3924 33.1768 34.0685 33.0418C35.0942 31.3684 35.7959 28.9393 36.1738 26.5371Z"
            fill="#FFF8E8"
          />
        </svg>
      </div>
      <ul class="nav-ancres">
        <li>
          <a href="#">Bar</a>
          <div></div>
        </li>
        <li>
          <a href="#">Kitchen</a>
          <div></div>
        </li>
        <li>
          <a href="#">Event</a>
          <div></div>
        </li>
        <li>
          <a href="#">Concept</a>
          <div></div>
        </li>
      </ul>
      <ul class="nav-infos">
        <li>
          <a href="#">Menu</a>
          <div></div>
        </li>
        <li>
          <a href="#">Book</a>
          <div></div>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
export default {
  name: "NavBar",
  components: {},
  data() {
    return {};
  },
  mounted() {
    gsap.fromTo(
      ".lvl_nav, .lvl_nav svg path",
      {
        color: "#464634",
        fill: "#464634",
      },
      {
        color: "#FFF8E8",
        fill: "#FFF8E8",
        ease: "power1.inOut",
        scrollTrigger: {
          trigger: ".fullScreen",
          start: "top top",
          end: "top+=90% top",
          scrub: true,
        },
      }
    );
    gsap.fromTo(
      ".lvl_nav, .lvl_nav svg path",
      {
        color: "#FFF8E8",
        fill: "#FFF8E8",
      },
      {
        color: "#464634",
        fill: "#464634",
        ease: "power1.inOut",
        scrollTrigger: {
          trigger: ".culture",
          start: "top-=50px top",
          end: "top top",
          scrub: true,
        },
      }
    );
    gsap.fromTo(
      ".lvl_nav li div",
      {
        background: "#FFF8E8",
      },
      {
        background: "#464634",
        ease: "power1.inOut",
        scrollTrigger: {
          trigger: ".culture",
          start: "top-=50px top",
          end: "top top",
          scrub: true,
        },
      }
    );
    gsap.fromTo(
      ".lvl_nav li div",
      {
        background: "#FFF8E8",
      },
      {
        background: "#464634",
        ease: "power1.inOut",
        scrollTrigger: {
          trigger: ".fullScreen",
          start: "top top",
          end: "top+=90% top",
          scrub: true,
        },
      }
    );

    document.querySelectorAll("nav li").forEach((el) => {
      el.addEventListener("mouseenter", () => {
        gsap.fromTo(
          el.querySelector("div"),
          {
            scaleX: 0,
          },
          {
            scaleX: 1,
            duration: 0.3,
            onComplete: () => {
              gsap.set(el.querySelector("div"), {
                transformOrigin: "right",
              });
            },
          }
        );
      });
      el.addEventListener("mouseleave", () => {
        gsap.to(el.querySelector("div"), {
          scaleX: 0,
          duration: 0.3,
          overwrite: "auto",
          onComplete: () => {
            gsap.set(el.querySelector("div"), {
              transformOrigin: "left",
            });
          },
        });
      });
    });
  },
  methods: {},
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";
nav {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  color: #fff8e8;
  font-family: "Manrope", sans-serif;
  text-transform: uppercase;
  padding: 0 40px;
  box-sizing: border-box;
  z-index: 19;
}
.lvl_nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  padding: 13px 0;
  box-sizing: border-box;
}
nav li {
  cursor: pointer;
  position: relative;

  & div {
    position: absolute;
    transform: scaleX(0);
    bottom: 0px;
    left: 0;
    display: block;
    width: 100%;
    height: 1px;
    background: variables.$red;
    transform-origin: left;
  }
}
.nav-ancres,
.nav-infos {
  display: flex;
  gap: 40px;
  font-size: 20px;
  font-weight: 300;
  padding: 20px 0;
}
</style>
