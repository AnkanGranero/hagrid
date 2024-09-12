<script setup>


import { ref, computed, onMounted } from "vue";

const gridSize = ref(15);
const itemsArray = ref([]);
const highlightX = ref(1);
const highlightY = ref(1);

function colorCalcDif(n, highlightedCoordinate) {

  let availableDistance = gridSize.value - 1;

  let numbers = [n, highlightedCoordinate];
  numbers.sort((a, b) => b - a);
  let high = numbers[0];
  let low = numbers[1];
  let difference = high - low;
  let percentageAway = difference / availableDistance;

  let invert = 250 * percentageAway;
  return 250 - invert;
};

function gridColor(item) {

  const { x, y } = item;
  return `background: rgb( ${colorCalcDif(x, highlightX.value)}, ${colorCalcDif(y, highlightY.value)}, 250)`

}

const gridStyling = computed(() => {
  return `grid-template-columns: repeat(${gridSize.value}, 1fr [col-start]);
  grid-template-rows: repeat(${gridSize.value}, 1fr);
`

})
function generateGridClass(item) {
  return `item item-y-${item.y} item-x-${item.x}`
}
function pos(item) {
  highlightX.value = item.x;
  highlightY.value = item.y;
}
onMounted(() => {

  let y = 1;

  for (let x = 1; x <= gridSize.value && y <= gridSize.value; x++) {

    itemsArray.value.push({ x, y })

    if (x == gridSize.value) {
      x = 0;
      y += 1;
    }


  }
})

</script>

<template>
  <div class="grid-container" :style="gridStyling">
    <div v-for="item in itemsArray" @mouseenter="pos(item)" :class="generateGridClass(item)" :style="gridColor(item)">
    </div>
  </div>
</template>

<style lang="scss" scoped>
.grid-container {
  display: grid;
  height: 50vw;
  width: 50vw;
}

.grid-wrapper {
  height: 120vh;
  width: 80vh;
  display: grid;
  grid-auto-rows: auto;
  height: 75%;
  width: 100%;

  @media only screen and (min-width: 768px) {
    height: 100%;
  }
}
</style>