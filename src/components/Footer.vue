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
      <img src="/src/assets/logo_main.svg" alt="logo Kurenai" />
      <div class="footer__bottom__credits">
        <span>© 2023 Kurenai</span>
        <span
          >Privacy policy / Terms & Conditions / Terms & conditions of use</span
        >
        <span>
          <a href="">Design by <strong>Noémie Heuzé</strong></a>
          <a href="">Dev by <strong>Lyman Abid</strong></a>
        </span>
      </div>
    </div>
  </footer>
</template>

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
</style>
