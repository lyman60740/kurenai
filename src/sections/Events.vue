<template>
  <section class="events" data-section-id="section3">
    <div class="events__wrapper" ref="wrapper">
      <div class="events__bandeau" ref="bandeau1">
        <span v-for="n in 5" :key="'bandeau1-' + n">/ Our event</span>
      </div>
      <div class="events__bandeau" ref="bandeau2">
        <span v-for="n in 5" :key="'bandeau2-' + n">/ Our event</span>
      </div>
    </div>

    <div class="events__slider" ref="slider" @click="handleSliderClick">
      <div class="events__slider__wrapper" ref="sliderWrapper">
        <div
          class="events__slider__item"
          v-for="event in eventItems"
          :key="event.title"
          :style="{ height: event.cardHeight }"
        >
          <img :src="event.img" alt="" />
          <div class="events__slider__item__text">
            <h2>{{ event.title }}</h2>
            <p>{{ event.date }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="kurenai-box">
      <svg
        class="kurenai-transi"
        width="812"
        height="169"
        viewBox="0 0 812 169"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M96.2839 166.226V169H69.204V166.226H73.3702L34.2548 101.03L22.2194 109.815V166.226H27.3113V169H0.462903V166.226H5.55484V10.8659L1.15726 12.7154L0 10.1724L22.2194 0V106.116L78.925 63.8085V63.5773C79.1564 63.3461 79.6194 62.4213 79.6194 61.4966C79.6194 59.8782 79.3879 58.9535 75.2218 58.9535H74.0645V55.948H94.2008L39.1153 97.3311H49.2992L90.4976 166.226H96.2839Z"
          fill="#FFF8E8"
        />
        <path
          d="M186.816 55.948V58.9535H181.492V166.226H186.816V169H164.828V163.451C159.042 167.15 152.561 169 145.617 169C145.386 169 145.386 169 145.155 169C137.517 168.769 130.11 166.457 124.092 161.833C119.695 158.596 115.992 154.204 113.677 149.349C111.131 144.494 109.742 138.945 109.742 133.397V58.9535H104.65V55.948H131.499V58.9535H126.407V147.268C126.638 153.279 129.416 158.596 134.045 162.064C137.285 164.607 141.22 165.995 145.155 165.995C145.386 165.995 145.386 165.995 145.617 165.995C152.561 165.995 159.273 163.914 164.828 159.752V58.9535H159.736V55.948H186.816Z"
          fill="#FFF8E8"
        />
        <path
          d="M276.337 75.5992C278.883 80.6854 280.04 86.2339 280.04 91.7825V93.4008H263.376V78.6046C263.376 78.3735 263.376 78.3735 263.376 78.1423C263.376 77.9111 263.376 77.6799 263.376 77.6799C263.144 71.6689 260.367 66.3516 255.738 62.6525C252.497 60.3406 248.563 58.9535 244.628 58.9535C244.628 58.9535 244.397 58.9535 244.165 58.9535C237.222 58.9535 230.51 61.0342 224.955 64.9644V166.226H230.047V169H203.198V166.226H208.29V58.9535H203.198V55.948H224.955V61.4966C230.741 57.7975 237.222 55.948 244.165 55.948C244.397 55.948 244.628 55.948 244.628 55.948C252.266 55.948 259.672 58.4911 265.69 63.1149C270.088 66.3516 273.791 70.7442 276.337 75.5992Z"
          fill="#FFF8E8"
        />
        <path
          d="M389.585 99.6429C394.446 102.186 398.612 105.885 401.621 110.971C406.713 119.988 406.944 130.622 401.852 139.639C399.769 143.338 397.455 146.806 394.677 150.042C389.586 155.822 383.336 160.446 376.161 163.914C368.986 167.15 361.348 169 353.248 169H352.785C344.684 169 336.815 167.15 329.408 163.914C322.233 160.446 315.984 155.822 310.892 150.042C301.634 139.639 296.773 126.23 296.773 112.59C296.773 98.7182 301.634 85.5404 310.892 75.1368C315.984 69.1259 322.233 64.502 329.408 61.2654C336.815 57.7975 344.684 55.948 352.785 55.948H353.248C361.348 56.1792 368.986 57.7975 376.161 61.2654C383.336 64.502 389.586 69.1259 394.677 75.1368C400.464 81.6101 404.63 89.4706 406.944 97.7934L407.407 99.6429H389.585ZM325.242 70.513C318.067 77.4487 313.901 86.6963 313.438 96.6375H392.132C391.437 86.6963 387.502 77.4487 380.327 70.513C372.921 63.1149 363.2 59.1847 352.785 58.9535C342.369 58.9535 332.417 63.1149 325.242 70.513ZM399.306 138.252C403.704 130.16 403.704 120.45 399.075 112.59C394.446 104.729 386.577 99.8741 377.781 99.6429H313.438V126.923C313.669 137.327 317.836 147.037 325.242 154.435C332.417 161.833 342.369 165.995 352.785 166.226C360.423 165.995 367.829 164.376 374.773 161.14C381.716 157.903 387.502 153.51 392.363 147.962C395.14 144.956 397.455 141.72 399.306 138.252Z"
          fill="#FFF8E8"
        />
        <path
          d="M500.642 166.226H505.966V169H478.886V166.226H483.978V77.6799C483.747 71.9001 480.969 66.3516 476.34 62.8837C473.1 60.5718 469.165 59.1847 465.23 59.1847C465.23 59.1847 464.999 59.1847 464.768 59.1847C457.824 59.1847 451.112 61.2654 445.557 65.1956V166.226H450.649V169H423.801V166.226H428.892V58.9535H423.801V55.948H445.557V61.7278C451.343 58.0287 457.824 56.1792 464.768 56.1792C464.999 56.1792 465.23 56.1792 465.23 56.1792C472.868 56.1792 480.275 58.7223 486.293 63.3461C490.69 66.5828 494.393 70.7442 496.939 75.5992C499.254 80.4542 500.411 85.3092 500.642 90.6265V166.226Z"
          fill="#FFF8E8"
        />
        <path
          d="M608.68 91.7825V166.226H613.772V169H591.784V147.037C591.552 147.73 591.089 148.424 590.858 149.118C588.312 154.204 584.609 158.365 580.211 161.833C573.731 166.688 566.093 169 558.223 169H557.76C550.122 169 542.716 166.457 536.698 161.833C532.301 158.596 528.598 154.435 526.052 149.58C523.506 144.494 522.348 138.945 522.348 133.166C522.348 127.386 523.506 121.837 526.052 116.982C528.598 112.127 532.301 107.735 536.698 104.498C537.161 104.036 537.856 103.573 538.55 103.111C537.161 99.4118 536.698 95.7127 536.698 91.7825C536.698 86.2339 538.087 80.6854 540.633 75.5992C542.948 70.7442 546.651 66.3516 551.048 63.1149C557.297 58.4911 564.704 55.948 572.573 55.948H573.036C580.906 55.948 588.081 58.4911 594.098 63.1149C598.496 66.3516 602.199 70.7442 604.745 75.5992C607.291 80.6854 608.68 86.2339 608.68 91.7825ZM591.784 132.703V89.2394C590.395 91.7825 588.312 94.0944 585.998 95.9439C582.063 98.7182 577.434 100.337 572.573 100.337H557.76C553.826 100.337 549.891 101.724 546.651 104.036C542.022 107.735 539.244 113.052 539.013 118.832C539.013 119.525 539.013 147.037 539.013 147.499C539.244 153.279 542.022 158.828 546.651 162.295C549.891 164.607 553.826 165.995 557.76 166.226C557.76 166.226 557.992 166.226 558.223 166.226C565.63 166.226 572.573 163.914 578.36 159.521C582.526 156.285 585.766 152.354 588.081 147.73C590.627 143.107 591.784 138.021 591.784 132.703ZM591.784 78.6046V77.6799C591.552 71.6689 588.775 66.3516 584.146 62.6525C580.906 60.3406 577.202 58.9535 573.036 58.9535C573.036 58.9535 572.805 58.9535 572.573 58.9535C565.398 58.9535 558.686 61.2654 552.9 65.4268C548.734 68.4323 545.493 72.3625 543.179 76.9863C540.864 81.6101 539.707 86.6963 539.707 91.7825C539.707 95.2503 540.17 98.487 541.096 101.492C546.188 98.7182 551.974 97.3311 557.76 97.3311H572.573C576.739 97.3311 580.906 95.9439 584.146 93.4008C588.775 89.933 591.552 84.6156 591.784 78.6046Z"
          fill="#FFF8E8"
        />
        <path
          d="M655.854 166.226H660.946V169H634.098V166.226H639.19V65.8892L634.792 67.9699L633.635 65.1956L655.854 55.0232V166.226ZM647.522 38.3776C642.893 38.3776 639.19 34.4473 639.19 29.8235C639.19 25.1997 642.893 21.5007 647.522 21.5007C652.151 21.5007 655.854 25.1997 655.854 29.8235C655.854 34.4473 652.151 38.3776 647.522 38.3776Z"
          fill="#FFF8E8"
        />
        <path
          d="M757.097 19.4378L722.379 84.5267L720.866 83.7264L755.583 18.6375L757.097 19.4378Z"
          fill="#FFF8E8"
        />
        <path
          d="M788.834 35.6655H810.332V37.7107H788.834V35.6655ZM786.831 67.3653H811V69.4549H786.831V67.3653ZM798.226 36.2435H800.407V68.4767H798.226V36.2435ZM779.532 50.8707H781.624V71.1443H779.532V50.8707ZM778.775 30.7305L780.822 31.6197C778.997 34.6874 776.505 38.5109 774.546 40.8228L772.944 40.067C774.902 37.6662 777.44 33.5759 778.775 30.7305ZM784.561 35.4877L786.609 36.4658C783.359 41.4008 778.641 47.7141 774.902 51.5821L773.389 50.6929C777.039 46.7804 781.802 40.2004 784.561 35.4877ZM770.585 38.9111L771.787 37.5773C774.591 39.8003 777.84 42.868 779.309 44.9576L778.152 46.5581C776.549 44.4241 773.389 41.1341 770.585 38.9111ZM783.537 45.4466L785.184 44.5575C787.543 47.3584 790.08 51.1819 791.149 53.6272L789.413 54.6498C788.389 52.1601 785.896 48.2476 783.537 45.4466ZM770.451 50.4261C774.858 50.2483 781.534 49.9371 788.255 49.5814L788.211 51.5376C781.802 51.8933 775.303 52.2934 770.674 52.5602L770.451 50.4261ZM784.873 56.0725L786.653 55.4945C788.211 58.251 789.68 61.9856 790.214 64.342L788.3 65.0534C787.766 62.6081 786.342 58.8735 784.873 56.0725ZM773.923 55.7613L776.06 56.117C775.259 60.3406 773.968 64.6088 772.365 67.4542C771.92 67.1874 770.986 66.6984 770.451 66.4761C772.143 63.7196 773.3 59.7182 773.923 55.7613Z"
          fill="#FFF8E8"
        />
      </svg>
    </div>
  </section>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Events",
  data() {
    return {
      eventItems: [
        {
          title: "Harami Nights",
          date: "April 20th 7:00pm",
          img: "/src/assets/header.webp",
          cardHeight: "632px",
        },
        {
          title: "Sake & Sushi Party",
          date: "April 20th 7:00pm",
          img: "/src/assets/header.webp",
          cardHeight: "540px",
        },
        {
          title: "Tokyo Mixology Lab",
          date: "April 20th 7:00pm",
          img: "/src/assets/header.webp",
          cardHeight: "700px",
        },
        {
          title: "Tokyo Mixology Lab",
          date: "April 20th 7:00pm",
          img: "/src/assets/header.webp",
          cardHeight: "632px",
        },
        {
          title: "Tokyo Mixology Lab",
          date: "April 20th 7:00pm",
          img: "/src/assets/header.webp",
          cardHeight: "632px",
        },
        {
          title: "Tokyo Mixology Lab",
          date: "April 20th 7:00pm",
          img: "/src/assets/header.webp",
          cardHeight: "632px",
        },
      ],
      currentIndex: 0,
      itemWidth: 560 + 163, // Largeur de l'élément + gap
    };
  },
  mounted() {
    gsap.to(".events", {
      scrollTrigger: {
        trigger: ".events",
        start: "bottom bottom",
        end: "bottom top",
        scrub: true,
        pin: true,
        pinSpacing: false,
      },
    });

    const wrapper = this.$refs.wrapper;
    const bandeau1 = this.$refs.bandeau1;

    const totalWidth = bandeau1.offsetWidth;

    const animateWrapper = () => {
      gsap.to(wrapper, {
        x: -totalWidth,
        duration: 30,
        ease: "none",
        repeat: -1,
        modifiers: {
          x: gsap.utils.unitize((x) => {
            return parseFloat(x) % totalWidth;
          }),
        },
      });
    };

    animateWrapper();

    // --------------- //

    document
      .querySelectorAll(".events__slider__item img")
      .forEach((element) => {
        element.addEventListener("mouseenter", (e) => {
          gsap.fromTo(
            slideButton,
            {
              border: "1px solid #B50B0C",
            },
            {
              border: "1px solid #FFF8E8",
            }
          );
          gsap.to(".slideButton svg path", {
            fill: "#FFF8E8",
            stroke: "#FFF8E8",
          });
        });

        element.addEventListener("mouseleave", (e) => {
          gsap.fromTo(
            slideButton,
            {
              border: "1px solid #FFF8E8",
            },
            {
              border: "1px solid #B50B0C",
            }
          );
          gsap.to(".slideButton svg path", {
            fill: "#B50B0C",
            stroke: "#B50B0C",
          });
        });
      });
  },
  methods: {
    handleSliderClick(event) {
      const slider = this.$refs.slider;
      const sliderWidth = slider.offsetWidth;
      const clickX = event.clientX - slider.getBoundingClientRect().left;

      if (clickX < sliderWidth / 2) {
        this.slideLeft();
      } else {
        this.slideRight();
      }
    },
    slideLeft() {
      const sliderWrapper = this.$refs.sliderWrapper;
      const firstItem = sliderWrapper.children[0];
      const rect = firstItem.getBoundingClientRect();

      if (rect.left >= 50) {
        console.log("Cannot slide left, already at the edge");
        return;
      }

      this.currentIndex = Math.max(this.currentIndex - 1, 0);
      this.animateSlider();
    },
    slideRight() {
      const sliderWrapper = this.$refs.sliderWrapper;
      const lastItem =
        sliderWrapper.children[sliderWrapper.children.length - 1];
      const rect = lastItem.getBoundingClientRect();
      const viewportWidth = window.innerWidth;

      if (rect.right <= viewportWidth - 50) {
        console.log("Cannot slide right, already at the edge");
        return;
      }

      this.currentIndex = Math.min(
        this.currentIndex + 1,
        this.eventItems.length - 1
      );
      this.animateSlider();
    },
    animateSlider() {
      const sliderWrapper = this.$refs.sliderWrapper;
      const targetX = -this.currentIndex * this.itemWidth;

      gsap.to(sliderWrapper, {
        x: targetX,
        duration: 1,
        ease: "power2.inOut",
      });
    },
  },
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";

.events {
  overflow: hidden;
  position: relative;
  // padding: 30vh 0 100svh 0;
  padding-top: 30vh;
  z-index: 1;
  &__wrapper {
    display: flex;
    position: absolute;
    width: max-content;
    will-change: transform;
  }
  &__bandeau {
    display: flex;
    white-space: nowrap;
    & span {
      padding: 0 10px;
      font-size: 120px;
      display: inline-block;
      flex-shrink: 0;
      font-family: variables.$bigilla;
      color: variables.$red;
      font-weight: bold;
      text-transform: uppercase;
    }
  }
  &__slider {
    margin-top: 300px;
    position: relative;
    width: 100%;
    cursor: pointer;
    padding: 0 40px;
    box-sizing: border-box;
    &__wrapper {
      display: flex;
      gap: 163px;
      will-change: transform;
    }
    &__item {
      display: flex;
      flex-direction: column;
      gap: 24px;
      width: 560px;
      flex: none;
      & img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
      & h2 {
        font-size: 20px;
        font-weight: 600;
      }
      &__text {
        display: flex;
        flex-direction: column;
        gap: 10px;
      }
    }
  }
}

.kurenai-box {
  width: 100%;
  height: 100svh;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 0 40px 128px 40px;
  box-sizing: border-box;
  z-index: -1;
  position: relative;
}
.kurenai-transi {
  width: 100%;
  height: auto;
  // width: calc(100% - 40px);
  & path {
    fill: variables.$red;
  }
}
</style>
