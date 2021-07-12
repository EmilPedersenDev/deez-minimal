<template>
  <div class="deez">
    <navbar />
    <Nuxt />
  </div>
</template>

<script>
import NavBar from "../components/NavBar.vue";
export default {
  name: "",
  components: {
    navbar: NavBar,
  },
  data() {
    return {};
  },
  methods: {},
  computed: {},
};
</script>

<style lang="scss" scoped>
.deez {
  width: 100%;
  height: 100%;
  position: relative;
}
</style>