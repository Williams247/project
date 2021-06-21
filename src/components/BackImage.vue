<template>
  <div>
    <div class="flip-card-back-image loader" ref="image_loader">
      Loading....
    </div>
    <img
      :src="image"
      class="hide flip-card-back-image"
      :alt="imgAlt"
      ref="image_view"
      @load="handleRevealImage"
    />
  </div>
</template>

<script>
export default {
  name: "BackImage",
  props: {
    image: String,
    imgAlt: String,
  },
  methods: {
    handleRevealImage() {
      this.$refs.image_loader.classList.add("hide");
      this.$refs.image_view.classList.remove("hide");
    },
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";
.flip-card-back-image {
  width: 100%;
  height: 210px;
  border-top-right-radius: $rounded;
  border-top-left-radius: $rounded;
}
.hide {
  display: none;
}

.loader {
  color: $grayed-doubled;
  font-size: 28px;
  font-weight: bold;
}
</style>
