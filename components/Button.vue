<template>
  <button
    class="e-button"
    @click="btnClick"
    :style="`min-width: ${minWidth}px`"
    :type="type"
    :disabled="disabled"
  >
    <!-- <img v-if="hasIcon" src="../../assets/icons/download.svg" alt="" /> -->
    <slot></slot>
    <!-- <e-spinner-simple v-if="isLoading" /> -->
  </button>
</template>

<script>
export default {
  name: "e-button",
  props: {
    minWidth: {
      type: String,
      default: "100",
    },
    hasIcon: {
      type: Boolean,
      default: true,
    },
    type: {
      type: String,
      default: "button",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    isLoading: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    btnClick(e) {
      this.$emit("click", e);
    },
  },
};
</script>

<style lang="scss" scoped>
.e-button {
  background-color: $purple-primary;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5px;
  padding: 10px 10px;
  transform: scale(1);
  transition: all ease 0.3s;
  box-shadow: none;
  color: $white;
  img {
    height: 25px;
    width: 25px;
  }
  span {
    letter-spacing: 1px;
    font-weight: 400;
  }

  &:hover:not(:disabled) {
    cursor: pointer;
    box-shadow: 0px 0px 15px 5px rgba(114, 50, 242, 0.4),
      0px 0px 15px 3px rgba(114, 50, 242, 0.4);
  }

  &:disabled {
    background: rgba(255, 255, 255, 0.1);
  }
}
</style>