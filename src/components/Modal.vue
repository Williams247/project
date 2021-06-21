<template>
  <div v-show="isModal" class="flex justify-content-center" id="modal">
    <div class="mt-4 pb-2" id="modal-box">
      <h1 class="pl-5 pr-5">
        {{ message }}
      </h1>
      <div class="flex justify-content-center">
        <div class="mt-2 pl-5 pr-5">
          <div @click="handleOpenCloseModal">
            <Button label="Close" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "./Button";

export default {
  name: "Modal",
  components: {
    Button,
  },
  props: {
    message: String,
    isModal: Boolean,
    handleOpenCloseModal: Function,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";

#modal {
  z-index: 18;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
  position: fixed;
  bottom: 0;
  #modal-box {
    background: $light;
    height: 250px;
    width: 90%;
    box-shadow: 0 0 58px #24242455;
    h1 {
      text-align: center;
    }
    @media (min-width: 780px) {
      width: 30%;
    }
  }
}
</style>
