<template>
  <button :class="[variant === 'primary' ? 'primary spacer':'danger spacer']">
   <span><i :class="icon"></i></span>
  </button>
</template>

<script>
 export default {
  name: 'FlatButton',
  props: {
   variant: String,
    icon: String
  }
 }
</script>

<style scoped lang="scss">
 @import "../styles/app.scss";
 .primary {
   background: $primary;
   color: $light;
 }
 .danger {
  background: $danger;
  color: $light
 }
 .spacer {
   cursor: pointer;
   padding-left: 39px;
   padding-right: 39px;
   padding-top: 3px;
   padding-bottom: 3px;
   border-radius: $rounded;
   font-size: 18px;
 }
</style>
