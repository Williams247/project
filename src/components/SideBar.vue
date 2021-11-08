<template>
  <div>
    <div>
      <img class="ml-1 pb-3 mt-3" src="../assets/logo.png" id="logo" />
    </div>
    <div class="flex" v-for="(item, index) in links.basic" :key="index">
      <div class="flex menu-list pt-2 pb-2 pr-2">
        <div class="icon"><i :class="item.icon"></i></div>
        <span class="text ml-sm-2 pl-1" style="padding-top: 1px">{{
          item.name
        }}</span>
      </div>
    </div>
    <p class="share-caption ml-1 pl-2">SHARE</p>
    <div class="mt-2">
      <div class="flex" v-for="(item, index) in links.share" :key="index">
        <div class="flex menu-list pt-2 pb-2 pr-2">
          <div class="icon"><i :class="item.icon"></i></div>
          <span class="text ml-sm-2 pl-1" style="padding-top: 1px">{{
            item.name
          }}</span>
        </div>
      </div>
    </div>
  </div>
</template> 

<script>
export default {
  name: "SideBar",
  props: {
    links: Object,
  },
};
</script>

<style scoped lang="scss">
@import "../styles/app.scss";
#logo {
  width: 130px;
  margin-top: 38px;
  margin-left: -12px;
  @media (min-width: 780px) {
    margin-left: 0;
  }
}
.menu-list {
  font-weight: bold;
  cursor: pointer;
  border-radius: 5px;
  border: 1px solid transparent;
  width: 70%;
  padding-left: 0;
  @media (min-width: 780px) {
    padding-left: 23px;
  }
  .text {
    color: $grayed-doubled;
    margin-left: 12px;
  }
  .icon {
    color: $grayed-doubled;
  }
  &:hover {
    border: 1px solid $grayed;
    .icon {
      color: $primary;
    }
    .text {
      color: $dark;
    }
  }
}
.share-caption {
  font-weight: bold;
}
</style>