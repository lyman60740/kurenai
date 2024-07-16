<template>
  <footer class="footer">
    <div class="footer__top">
      <div class="footer__top__bloc">
        <div class="footer__top__bloc__label">
          <h3>/ Meet us</h3>
        </div>
        <span>Gerrard Street</span>
        <span>London W1D 5PT • UK</span>
      </div>

      <div class="footer__top__bloc">
        <div class="footer__top__bloc__label">
          <h3>/ Openning hours</h3>
        </div>
        <span>Mon — Fri • 11:30 — 19:00</span>
        <span>Sat — Sun • 14:00 — 21:00</span>
      </div>

      <div class="footer__top__bloc">
        <div class="footer__top__bloc__label">
          <h3>/ Contact us</h3>
        </div>
        <span>hello@kurenai.com</span>
        <span>(+48) 567 890 12</span>
      </div>

      <div class="footer__top__bloc">
        <div class="footer__top__bloc__label">
          <h3>/ Follow us</h3>
        </div>
        <span>@kurenai</span>
        <span>@kurenai</span>
        <span>@kurenai</span>
      </div>
    </div>

    <div class="footer__bottom">
      <img
        class="kurenai_transi_end"
        src="/src/assets/logo_main.svg"
        alt="logo Kurenai"
      />
      <div class="footer__bottom__credits">
        <span>© 2023 Kurenai</span>
        <span
          >Privacy policy / Terms & Conditions / Terms & conditions of use</span
        >
        <span>
          <a href="https://www.linkedin.com/in/noemieheuze/"
            >Design by <u>Noémie Heuzé</u></a
          >
          <a href="https://lyman.fr/">Dev by <u>Lyman Abid</u></a>
        </span>
      </div>
    </div>
  </footer>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Footer",
  data() {
    return {};
  },
  mounted() {
    gsap.to(".kurenai_transi_end", {
      y: 0,
      ease: "none",
      scrollTrigger: {
        trigger: ".kurenai_transi_end",
        start: "bottom+=120px bottom",
        endTrigger: "html",
        end: "bottom bottom",
        scrub: true,
      },
    });

    gsap.fromTo(
      ".lvl_nav",
      {
        pointerEvents: "auto",
        autoAlpha: 1,
      },
      {
        pointerEvents: "none",
        autoAlpha: 0,
        scrollTrigger: {
          trigger: ".footer",
          start: "top-=50px top",
          end: "top top",
          scrub: true,
        },
      }
    );

    const tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".footer",
        start: "top-=150px top",
        end: "bottom bottom",
        toggleActions: "play none none reverse",
      },
    });
    tl.from(".footer__top .footer__top__bloc", {
      yPercent: -100,
      autoAlpha: 0,
      stagger: 0.2,
      duration: 0.8,
      ease: "power3.out",
    }).from(
      ".footer__bottom .footer__bottom__credits",
      {
        yPercent: 100,
        autoAlpha: 0,
        duration: 1,
        ease: "power3.out",
      },
      "<75%"
    );
  },
};
</script>

<style scoped lang="scss">
@use "/src/styles/variables";
.footer {
  width: 100%;
  height: 100svh;
  background: variables.$red;
  color: variables.$white;
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 40px;
  box-sizing: border-box;
  position: relative;
  z-index: 5;
  overflow: hidden;
  &__top {
    display: flex;
    gap: 80px;
    &__bloc {
      display: flex;
      flex-direction: column;
      gap: 10px;
      &__label {
        & h3 {
          font-size: 20px;
          font-weight: 300;
        }
      }
      & span {
        font-size: 20px;
        font-weight: 300;
        text-transform: uppercase;
      }
    }
  }
  &__bottom {
    display: flex;
    flex-direction: column;
    gap: 80px;
    &__credits {
      display: flex;
      justify-content: space-between;
      font-size: 16px;
      font-weight: 200;
      & a {
        color: variables.$white;
        // text-decoration: underline;
      }
      & span:nth-child(3) {
        display: flex;
        gap: 20px;
      }
    }
  }
}
.kurenai_transi_end {
  transform: translateY(-100svh);
}
</style>
