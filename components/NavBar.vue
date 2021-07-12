<template>
  <header>
    <nav class="navigation">
      <img src="/deez-minimal/acorn.png" alt="Deez logo" />
      <ul v-if="desktop" class="navigation-links">
        <li class="navigation-links__item">
          <NuxtLink to="/" class="navigation-links__item-link">Home </NuxtLink>
        </li>
        <li class="navigation-links__item">
          <NuxtLink to="/second-hand" class="navigation-links__item-link"
            >Second Hand
          </NuxtLink>
        </li>
        <li class="navigation-links__item">
          <NuxtLink to="/outlet" class="navigation-links__item-link"
            >Outlet
          </NuxtLink>
        </li>
        <li class="navigation-links__item">
          <NuxtLink to="/about" class="navigation-links__item-link"
            >About
          </NuxtLink>
        </li>
      </ul>
      <div
        v-if="!desktop"
        ref="navigationBtn"
        class="navigation__icon-wrapper"
        @click="toggleMenu"
      >
        <div class="navigation__hamburger"></div>
      </div>
      <div ref="menuOverlay" class="navigation-overlay">
        <ul class="navigation-overlay__links">
          <li class="navigation-overlay__link">
            <NuxtLink to="/">Home </NuxtLink>
          </li>
          <li class="navigation-overlay__link">
            <NuxtLink to="/second-hand">Second Hand </NuxtLink>
          </li>
          <li class="navigation-overlay__link">
            <NuxtLink to="/outlet">Outlet </NuxtLink>
          </li>
          <li class="navigation-overlay__link">
            <NuxtLink to="/about">About </NuxtLink>
          </li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "navbar",
  data() {
    return {
      innerWidth: 0,
      isOpen: false,
    };
  },
  mounted() {
    this.innerWidth = window.innerWidth;
    window.addEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.innerWidth = window.innerWidth;
      console.log(this.innerWidth);
    },
    toggleMenu() {
      this.isOpen = !this.isOpen;
      let navBtn = this.$refs.navigationBtn;
      let navOverlay = this.$refs.menuOverlay;
      let body = document.querySelector("body");

      if (this.isOpen) {
        navBtn.classList.add("open");
        navOverlay.classList.add("open");
        body.style.overflowY = "hidden";
      } else {
        navBtn.classList.remove("open");
        navOverlay.classList.remove("open");
      }
    },
  },
  computed: {
    desktop() {
      return this.innerWidth > 768;
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  width: 100%;
  position: absolute;
  top: 0;
  z-index: 2;
  nav {
    width: 100%;
    @media (min-width: 768px) {
      padding: 20px 100px;
    }
    padding: 20px 20px;

    display: flex;
    justify-content: space-between;

    img {
      @media (min-width: 768px) {
        width: 60px;
      }
      width: 50px;
      height: 100%;
    }
    ul {
      margin: 0;
      &.navigation-links {
        display: flex;
      }
      li {
        list-style-type: none;
        margin: 0;
        padding: 0;
        margin-right: 20px;
        &:last-child {
          margin: 0;
        }
      }
    }

    a {
      position: relative;
      text-decoration: none;
      color: $black;
      font-weight: 400;
      &::before {
        transition: width 0.3s ease-in-out, opacity 0.3s ease;
        content: "";
        position: absolute;
        bottom: -2px;
        left: 0;
        background: $black;
        width: 0px;
        height: 0px;
        opacity: 0;
      }
      &:hover {
        &::before {
          opacity: 1;
          height: 2px;
          width: 100%;
        }
      }

      &.navigation-links__item-link {
        &:hover {
          &::before {
            height: 1.2px !important;
          }
        }
      }
    }

    .navigation__icon-wrapper {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      padding-right: 12px;
      z-index: 2;
      @media (min-width: 768px) {
        justify-content: center;
        padding: 0;
        width: 40px;
        height: 30px;
      }
      &:hover {
        cursor: pointer;
      }

      .navigation__hamburger {
        height: 2px;
        width: 15px;
        border-radius: 5px;
        background: $black;
        box-shadow: 0px 2px 5px rgba(255, 101, 47, 0.2);
        @include ease(0.3s);
        @media (min-width: 768px) {
          width: 20px;
        }
        &::before,
        &::after {
          content: "";
          position: absolute;
          @media (min-width: 768px) {
            width: 30px;
          }
          width: 25px;
          height: 2px;
          background: $black;
          border-radius: 5px;
          transition: all 0.3s ease;
          box-shadow: 0px 2px 5px rgba(255, 101, 47, 0.2);
        }

        &::before {
          transform: translateY(-9px);
          @media (min-width: 768px) {
            transform: translateY(-12px);
          }
        }

        &::after {
          transform: translateY(9px);
          @media (min-width: 768px) {
            transform: translateY(12px);
          }
        }
      }

      &.open {
        .navigation__hamburger {
          transform: translateX(-50px);
          background: transparent;
          box-shadow: none;
          &::before {
            background: $black !important;
            transform: rotate(45deg) translate(35px, -35px);
          }
          &::after {
            background: $black !important;
            transform: rotate(-45deg) translate(35px, 35px);
          }
        }
      }
    }

    .navigation-overlay {
      position: absolute;
      width: 0;
      height: 100vh;
      right: 0;
      top: 0;
      visibility: hidden;
      overflow: hidden;
      background: $beige;
      @include ease(0.5s);
      opacity: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      &.open {
        width: 100%;
        visibility: visible;
        opacity: 1;
        ul {
          margin: 0;
          padding: 0;

          li {
            list-style-type: none;
            padding: 0;
            margin: 0;
            a {
              font-size: 2rem;
            }
          }
        }
      }
    }
  }
}
</style>