<template>
  <button :disabled="loading" class="button pt-2 pb-2 pl-4 pr-4">
    <span v-show="loading === true"> Loading.. </span>
    <span v-show="loading === false">
      {{ label }}
    </span>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    label: String,
    loading: Boolean,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";
.button {
  background: $primary;
  color: $light;
  border-radius: $rounded;
  padding-top: 8px;
  margin-top: -23px;
  padding-bottom: 8px;
  cursor: pointer;
  transition: 333ms ease;
  &:hover {
    background: $primary-hovered;
  }
}
</style>
