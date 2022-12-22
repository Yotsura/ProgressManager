<script setup lang="ts">
import { ref, computed } from 'vue';
const props = defineProps({
  maxVal:{type: Number, required:true},
  height: Number
});

const progressPercent = computed ( ()=> {
  return 100 * progress.value / props.maxVal;
});
const barColor = computed (() => {
  if (progressPercent.value == 100)
    return "gold";
  else if (70 <= progressPercent.value && progressPercent.value < 100)
    return "goldenrod";
  else if (40 <= progressPercent.value && progressPercent.value < 70)
    return "darkgoldenrod";
  else if (20 <= progressPercent.value && progressPercent.value < 40)
    return "orangered";
  else
  return "red";
})

const progress = ref(0);

const addCnt = () => {
  if(progress.value < props.maxVal)
    progress.value++;
}
const reduceCnt = () => {
  if(progress.value > 0)
    progress.value--;
}
</script>
<template>
  <div class="progress" :style="`width:${progressPercent}%; background-color:${barColor}`">
  </div>
  <div class="bar"></div>
  <div>
    <div class="d-flex btn-group">
      <div class="btn progress-btn d-flex justify-content-center" @click="reduceCnt">-</div>
      <div class="btn progress-btn d-flex justify-content-center" @click="addCnt">+</div>
    </div>
  </div>
</template>

<style scoped>
.bar{
  position: relative;
  background-color: white;
  width: 100%;
  height: 10px;
  z-index: 100;
}
.progress{
  position: absolute;
  height: 10px;
  z-index: 101;
    -webkit-transition: all 0.3s;
    -moz-transition: all 0.3s;
    -ms-transition: all 0.3s;
    -o-transition: all 0.3s;
	transition: all 0.3s;
}

.progress-btn{
	font-weight: 400;
  width: 100%;
	user-select: none;
	color: white;
	background-color: transparent;
	border: 1px solid white;
	padding: 0.375rem 0.75rem;
	border-radius: 0.25rem;
}
</style>