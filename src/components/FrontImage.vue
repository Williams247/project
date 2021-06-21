<template>
  <div>
    <div class="flip-card-front-image loader" ref="image_loader">
      Loading....
    </div>
    <img
      :src="image"
      class="flip-card-front-image hide"
      :alt="imgAlt"
      ref="image_view"
      @load="handleRevealImage"
    />
  </div>
</template>

<script>
export default {
  name: "FrontImage",
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
.flip-card-front-image {
  width: 100%;
  height: $card-height;
  border-radius: $rounded;
}
.hide {
  display: none;
}

.loader {
  color: $light;
  font-size: 28px;
  margin-top: 95px;
}
</style>
