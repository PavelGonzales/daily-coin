<template lang="pug">
  v-app(light)
    v-toolbar
      v-toolbar-title(v-text="title")
    router-view
</template> 

<script>
  export default {
    data() {
      return {
        title: 'Daily Coin',
      };
    },
  };
</script>

<style lang="stylus">
  @import './stylus/main'
</style>
