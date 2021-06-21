<template>
  <div>
    <div id="close" @click="showMobileMenu">
      <i class="fa fa-close"></i>
    </div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "MobileMenu",
  props: {
    showMobileMenu: Function,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";
#close {
  color: $grayed;
  padding-top: 23px;
  padding-left: 69%;
}
</style>