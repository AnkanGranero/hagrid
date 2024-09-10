<script setup>
import Grid from './Grid.vue';



defineProps({
  theme: String,
})




</script>

<template>
  <div class="tv-wrapper"
  >
  <Grid />
</div>
  
</template>

<style lang="scss" scoped>
.tv-wrapper {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  @media only screen and (min-width: $tablet) {

  }

}

</style>
