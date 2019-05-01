<template>
    <div id="tiny-footer">
      <h6>Made in the U.S.A.</h6>
      <h6>Jeremy Fields 2019</h6>
      <h6>Thanks for passing through</h6>
    </div>
</template>

<script>

export default {
  name: 'tiny-footer'
};
</script>

<style scoped lang="sass">
@import "../assets/style/_myold.sass"

#tiny-footer
  @include tiny-flex
  @include news-cycle
  font-size: 10px
  background-color: white
  // Crappy workaround, don't really want this fixed
  //position: fixed
  //bottom: 0
  //left: 0
  //right: 0

  
</style>
