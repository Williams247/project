<template>
  <div>
    <Layout />
  </div>
</template>

<script>
  import Layout from './layout/layout';

  export default {
    name: 'App',
    components: {
      Layout
    }
  }
</script>

<style lang="scss">
  @import './styles/app.scss';
</style>