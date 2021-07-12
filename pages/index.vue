<template>
  <div class="home">
    <div class="deez-information">
      <div class="deez-information__wrapper">
        <h1 :class="{ active: isMounted }">Deez</h1>
        <p :class="{ active: isMounted }">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. In
          accusantium soluta itaque odit voluptate molestiae et dicta
          consectetur, debitis, excepturi eos iusto autem praesentium! Soluta a
          sapiente numquam officiis modi.
        </p>
        <d-button :class="{ active: isMounted }">About us</d-button>
      </div>
    </div>
    <div class="shopping-animation">
      <div class="shopping-animation__wrapper">
        <lottie-shopping />
      </div>
    </div>
    <div class="brands">
      <img class="hm" src="/deez-minimal/hm.png" alt="" />
      <img class="boozt" src="/deez-minimal/boozt.png" alt="" />
      <img class="zalando" src="/deez-minimal/zalando.png" alt="" />
    </div>
  </div>
</template>

<script>
import LottieAnimationShopping from "../components/Lottie-shopping.vue";
export default {
  components: {
    LottieAnimationShopping,
  },
  data() {
    return {
      isMounted: false,
    };
  },
  mounted() {
    this.isMounted = true;
  },
};
</script>
<style lang="scss" scoped>
.home {
  height: 100vh;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
  position: relative;
  overflow: hidden;
  @media (max-width: 768px) {
    padding: 0 20px;
  }

  .deez-information {
    width: 100%;
    display: flex;
    justify-content: center;
    flex-basis: 100%;
    @media (min-width: 768px) {
      align-self: flex-end;
    }
    @media (min-width: 1050px) {
      flex: 1;
      flex-basis: 0%;
      align-self: center;
    }

    .deez-information__wrapper {
      h1,
      p,
      .e-button {
        transition: all 0.8s ease 0.6s;
        transform: translateY(400px);
        opacity: 0;
        visibility: hidden;
        &.active {
          transform: translateY(0);
          opacity: 1;
          visibility: visible;
        }
      }
      h1 {
        position: relative;
        transition: all 0.8s ease 0.4s;

        &::before {
          content: "";
          position: absolute;
          width: 30px;
          height: 1.5px;
          background: $purple-primary;
          top: -10px;
          @media (min-width: 768px) {
            left: -10px;
          }
        }
      }

      p {
        transition: all 0.8s ease 0.6s;
        margin: 20px 0px 30px;
      }
      .e-button {
        transition: transform 0.8s ease 0.7s, box-shadow 0.3s ease;
      }
      max-width: 400px;
    }
  }
  .shopping-animation {
    width: 100%;
    display: none;
    justify-content: center;
    flex-basis: 100%;
    align-self: flex-start;
    @media (min-width: 1050px) {
      flex: 1;
      flex-basis: 0%;
      align-self: center;
    }

    @media (min-width: 768px) {
      display: flex;
    }

    .shopping-animation__wrapper {
      width: 100%;
    }
  }

  .brands {
    position: absolute;
    bottom: 20px;
    left: 50%;
    width: 100%;
    max-width: 300px;
    transform: translateX(-50%);
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    img {
      width: 60px;
      height: 100%;
      &.hm {
        width: 50px;
        filter: contrast(0.2);
      }
      &.boozt {
        filter: contrast(0.3);
      }
    }
  }
}
</style>
