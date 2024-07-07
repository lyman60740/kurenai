<template>
  <section class="events">
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
  </section>
</template>

<script>
import gsap from "gsap";

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
      const targetX = -this.currentIndex * this.itemWidth + 50;

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
  padding-top: 200px;
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
</style>
