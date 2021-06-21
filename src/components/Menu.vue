<template>
  <div id="menu">
    <div class="flex flex-direction-row-column" id="menu-items-container">
      <div class="menu" v-for="(item, index) in menus" :key="index">
        <div
          :class="[
            index === 6
              ? 'menu-item-plan flex justify-content-center'
              : 'menu-item flex justify-content-center',
          ]"
        >
          {{ item }}
          <div class="menu-icon"><i class="fa fa-chevron-down"></i></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SampleMenu from "../constants/sample-menus.json";
export default {
  name: "Menu",
  data() {
    return {
      menus: SampleMenu,
    };
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";

#menu {
  margin-top: 23px;
  .menu-icon {
    font-size: 9px;
    margin-top: 2px;
    margin-left: 9px;
  }
}

#menu-items-container {
  width: 100%;
  box-shadow: 0 0 18px#e1e1e4;
  border-radius: $rounded;
  @media (min-width: 780px) {
    width: 75%;
  }
  .menu-item {
    width: 100%;
    text-align: left;
    cursor: pointer;
    font-size: 13.5px;
    padding-top: 13px;
    padding-bottom: 13px;
    border-right: 1px solid transparent;
    @media (min-width: 780px) {
      width: 113px;
      text-align: center;
      border-right: 1px solid $grayed;
    }
    &:hover {
      color: $primary;
    }
    span {
      margin-left: 6px;
    }
  }
  .menu-item-plan {
    width: 100%;
    text-align: left;
    cursor: pointer;
    font-size: 13.5px;
    padding-top: 13px;
    padding-bottom: 13px;
    border-right: 1px solid transparent;
    @media (min-width: 780px) {
      width: 113px;
      text-align: center;
    }
    &:hover {
      color: $primary;
    }
    span {
      margin-left: 6px;
    }
  }
}
</style>
