<script setup>


defineProps({
  theme: String,
})




</script>

<template>
  <div class="tv-wrapper"
  >
</div>
  
</template>

<style lang="scss" scoped>
.tv-wrapper {
  height: 100%;
  width: 100%;
  position: fixed;
  @media only screen and (min-width: $tablet) {
    position: unset;
    height: 85%;
    width: unset;
    margin: 0 14%;
  }

}

</style>
