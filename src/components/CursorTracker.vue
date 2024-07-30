<template>
  <div ref="cursorTracker" class="cursor-tracker">
    <div class="tracker-content">
      <!-- Utilisation de v-if pour afficher du contenu dynamique basé sur la section survolée -->
      <div v-if="currentSection === 'section1'" class="discover-button">
        <span
          >Discover <br />
          bar</span
        >
        <svg
          width="32"
          height="16"
          viewBox="0 0 32 16"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M0 8H32M32 8C27.5817 8 24 4.41828 24 0M32 8C27.5817 8 24 11.5817 24 16"
            stroke="#464634"
          />
        </svg>
      </div>

      <div class="ourmenu-button" v-if="currentSection === 'section2'">
        <span
          >OUR<br />
          MENU</span
        >
        <svg
          width="32"
          height="16"
          viewBox="0 0 32 16"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M0 8H32M32 8C27.5817 8 24 4.41828 24 0M32 8C27.5817 8 24 11.5817 24 16"
            stroke="#464634"
          />
        </svg>
      </div>

      <div class="slideButton" v-if="currentSection === 'section3'">
        <svg
          width="32"
          height="16"
          viewBox="0 0 32 16"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M0 8H32M32 8C27.5817 8 24 4.41828 24 0M32 8C27.5817 8 24 11.5817 24 16"
            stroke="#464634"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "CursorTracker",
  data() {
    return {
      mouseX: 0,
      mouseY: 0,
      currentSection: null,
    };
  },
  mounted() {
    this.initCursorTracker();
    this.initSectionListeners();
    this.initSlideLogic();
  },
  methods: {
    initSlideLogic() {
      const eventBox = document.querySelector(".events");
      if (!eventBox) {
        console.error("events__slider element not found");
        return;
      }

      const throttle = (func, limit) => {
        let lastFunc;
        let lastRan;
        return function () {
          const context = this;
          const args = arguments;
          if (!lastRan) {
            func.apply(context, args);
            lastRan = Date.now();
          } else {
            clearTimeout(lastFunc);
            lastFunc = setTimeout(function () {
              if (Date.now() - lastRan >= limit) {
                func.apply(context, args);
                lastRan = Date.now();
              }
            }, limit - (Date.now() - lastRan));
          }
        };
      };

      const handleMouseMove = (e) => {
        const slideButton = document.querySelector(".slideButton");
        if (!slideButton) {
          console.error(".slideButton element not found");
          return;
        }

        const slideButtonSvg = slideButton.querySelector("svg");
        if (!slideButtonSvg) {
          console.error("SVG inside .slideButton element not found");
          return;
        }

        this.mouseX = e.pageX;
        this.mouseY = e.pageY;

        const boxWidth = eventBox.offsetWidth;
        const boxLeft = eventBox.getBoundingClientRect().left;

        // Déterminer la position du curseur par rapport à la largeur de event__slider
        const cursorPosition = this.mouseX - boxLeft;
        const rotation = cursorPosition < boxWidth / 2 ? -180 : 0;

        gsap.to(slideButtonSvg, {
          rotate: rotation,
          duration: 0.8,
          ease: "power3.out",
        });
      };

      const throttledMouseMove = throttle(handleMouseMove, 100);

      eventBox.addEventListener("mousemove", throttledMouseMove);

      eventBox.addEventListener("mouseenter", () => {
        gsap.fromTo(
          slideButton,
          {
            autoAlpha: 0,
          },
          {
            autoAlpha: 1,
          }
        );
      });

      eventBox.addEventListener("mouseleave", () => {
        gsap.fromTo(
          slideButton,
          {
            autoAlpha: 1,
          },
          {
            autoAlpha: 0,
          }
        );
      });
    },
    initCursorTracker() {
      const cursorTracker = this.$refs.cursorTracker;

      const updatePosition = (e) => {
        this.mouseX = e.clientX;
        this.mouseY = e.clientY;

        gsap.to(cursorTracker, {
          x: this.mouseX + 90 + "px",
          y: this.mouseY + 90 + "px",
          duration: 0.3,
          ease: "power2.out",
        });
      };

      document.addEventListener("mousemove", updatePosition);
    },
    initSectionListeners() {
      const sections = document.querySelectorAll("[data-section-id]");

      sections.forEach((section) => {
        section.addEventListener("mouseenter", () => {
          this.currentSection = section.getAttribute("data-section-id");
          gsap.to(".cursor-tracker", {
            opacity: 1,
            duration: 0.3,
            ease: "power2.out",
          });
        });

        section.addEventListener("mouseleave", () => {
          this.currentSection = null;
          gsap.to(".cursor-tracker", {
            opacity: 0,
            duration: 1.2,
            ease: "power2.out",
          });
        });
      });
    },
  },
};
</script>

<style lang="scss">
@use "/src/styles/variables";

.cursor-tracker {
  position: fixed;
  top: 0;
  left: 0;
  width: 175px;
  height: 175px;
  pointer-events: none;
  transform: translate(-50%, -50%);
  z-index: 15;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.discover-button {
  border: 1px solid variables.$red;
  pointer-events: none;
  opacity: 0;
  & span {
    color: variables.$red;
  }
}
.ourmenu-button {
  height: 175px;
  width: 175px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 16px;
  will-change: transform;
  pointer-events: none;
  z-index: 15;
  background: variables.$red;
  & span {
    font-size: 20px;
    font-weight: 300;
    text-transform: uppercase;
    line-height: 30px;
    text-align: center;
    color: variables.$white;
    transform: translateY(15%);
  }
}

.slideButton {
  border: 1px solid variables.$red;
  pointer-events: none; /* S'assure que l'élément ne bloque pas les événements de la souris */
  height: 175px;
  width: 175px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  will-change: transform;
  z-index: 1500;
  opacity: 1;
}
</style>
