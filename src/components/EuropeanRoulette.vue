<template>
  <div class="all-numbers">
    <div id="number-box-0" :style="ceroStyles">{{ rouletteNumbers[0].value }}</div>
    <div class="numbers" :style="{width:(100/14)*12+'%'}">
      <div
        v-for="number in boardOrder"
        :key="number"
        :id="'number-box-' + number"
        :style="{ ...numbersStyles, backgroundColor: rouletteNumbers[number].color }"
        >
          {{ rouletteNumbers[number].value }}
      </div>
    </div>
    <div class="lines" :style="{ width: 100 / 14 + '%' }">Line</div>
  </div>
</template>

<script setup>
import { numbers } from '@/assets/numbers.js'
import { ref } from 'vue'

const rouletteNumbers = ref([])
rouletteNumbers.value = numbers

const ceroStyles = {
  backgroundColor: 'green',
  color: 'white',
  width: 100 / 14 + '%',
  display: 'flex',
  justifyContent: 'center',
  alignItems: 'center',
  border: 'solid 1px white'
}

const numbersStyles = {
  color: 'white',
  width: 100 / 12 + '%',
  display: 'flex',
  justifyContent: 'center',
  alignItems: 'center',
  border: 'solid 1px white'
}

const boardOrder = [
  3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 2, 5, 8, 11, 14, 17, 20, 23, 26, 29, 32, 35, 1, 4, 7,
  10, 13, 16, 19, 22, 25, 28, 31, 34
]
</script>

<style scoped>
.numbers {
  display: flex;
  flex-wrap: wrap;
}

.all-numbers {
  display: flex;
  width: 100%;
  height: 200px;
}

.lines {
  border: solid 1px white;
}
</style>
