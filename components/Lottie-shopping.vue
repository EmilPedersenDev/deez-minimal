<template>
  <lottie
    class="shopping-animation"
    :options="lottieOptions"
    v-on:animCreated="handleAnimation"
  />
</template>

<script>
import lottie from "vue-lottie/src/lottie.vue";
import * as animationData from "~/assets/animations/shopping-lottie.json";
export default {
  name: "lottie-shopping",
  components: {
    lottie,
  },
  data() {
    return {
      anim: null,
      lottieOptions: { animationData: animationData.default },
    };
  },
  methods: {
    handleAnimation(anim) {
      this.anim = anim;
    },
  },
};
</script>

<style lang="scss" scoped>
.shopping-animation {
  max-width: 200px;
  @media (min-width: 1050px) {
    max-width: 500px;
  }
}
</style>