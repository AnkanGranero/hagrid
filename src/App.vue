<script setup>
import Tv from './components/Tv.vue';
import Grid from './components/Grid.vue';
</script>

<template>
  <Tv />
</template>

<style lang="scss" >

html {

  height: 100%;
  margin: 0;

}
body {
  -webkit-user-select: none;
  height: 100%;
  width: 100%;
  min-height: 100%;
  margin: 0;
  min-width: fit-content;
  min-height: fit-content;
  background: $hagrid-green;

  margin: 0;

  font-size: 1.5rem;
  letter-spacing: -1px;
  font-family: "Open Sans", sans-serif;
}

#app {
  height: 100%;
}
</style>
