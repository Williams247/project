<template>
  <div v-show="loading" class="flex justify-content-center" id="loader-modal">
    <div>
      <div id="loader"></div>
      <h2 class="mt-5">Loading....</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "Loader",
  props: {
    loading: Boolean,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";

#loader-modal {
  background: $light;
  width: 100%;
  height: 100%;
  z-index: 222;
  bottom: 0;
  position: fixed;
  #loader {
    width: 65px;
    height: 65px;
    border-top: 23px solid $grayed;
    border-bottom: 23px solid $grayed;
    border-left: 23px solid transparent;
    border-right: 23px solid transparent;
    border-radius: $absolutely-round;
    margin-top: 188px;
    animation-name: rotate;
    animation-iteration-count: infinite;
    animation-play-state: running;
    animation-duration: 1s;
  }

  @keyframes rotate {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
}
</style>
