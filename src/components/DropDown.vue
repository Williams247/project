<template>
  <div id="dropdown">
    <div v-for="(item, index) in dropdownItems" :key="index">
      <div :class="[index === 2 ? 'flex pl-5 pr-5 pt-2 pb-2':'flex pl-5 pr-5 pt-2 pb-2 single-menu-list']">
        <div class="pane-1">
            <img src="../assets/lady.jpg" class="dropdown-image" />
        </div>
        <div class="heading-container">
            <div class="heading">{{ item.text.heading }}</div>
            <div class="caption">{{ item.text.caption }}</div>
        </div>
        <div>
            <div :class="[item.color === 'grayed-darken' ? 'grayed-darken':'danger']">
                <i :class="item.icon"></i>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import dropDownData from "../constants/sample-notification.json";
export default {
  name: "DropDown",
  data() {
    return {
      dropdownItems: dropDownData,
    };
  },
};
</script>

<style scoped lang="scss">
@import '../styles/app.scss';
 #dropdown {
   font-size: 13px;
   .single-menu-list {
     border-bottom: 1px solid $grayed;
   }
   .dropdown-image {
      width: 40px;
      height: 40px;
      border-radius: $absolutely-round;
   }
   .heading-container {
    width: 90%;
    text-align: center;
     .heading {
       color: $grayed-doubled;
       font-size: 14px;
       font-weight: bold;
     }
     .caption {
       font-size: 10px;
     }
   }
   .grayed-darken {
     color: $grayed-doubled
   }
   .danger {
    color: $danger
   }
 }
</style>
