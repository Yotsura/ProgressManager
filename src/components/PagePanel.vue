<script setup lang="ts">
import { ref, computed } from 'vue';
import ProgressBarVue from './ProgressBar.vue';

const props = defineProps({
  pagetitle:{type: String, required:true}
});

const progress = ref(0);
const maxVal = ref(7)
const addCnt = () => {
  if(progress.value < maxVal.value)
    progress.value++;
}
const reduceCnt = () => {
  if(progress.value > 0)
    progress.value--;
}
</script>

<template>
  <div class="col-md-2 col-3">
    <div class="border panel">
      <ProgressBarVue :maxVal="maxVal" :height="10" />
      <div class="d-flex btn-group">
        <!-- <div class="btn panel-btn d-flex justify-content-center" @click="reduceCnt">-</div>
        <div class="btn panel-btn d-flex justify-content-center" @click="addCnt">+</div> -->
      </div>
      <div v-text="pagetitle" class="d-flex panel-txt"></div>
    </div>
  </div>
</template>

<style>
.panel-btn{
	font-weight: 400;
	user-select: none;
	color: white;
	background-color: transparent;
	border: 1px solid white;
	padding: 0.375rem 0.75rem;
	border-radius: 0.25rem;
	transition: color .15s ease-in-out,background-color .15s ease-in-out,border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}

.panel-txt{
  position: absolute;
  bottom: 0.1rem;
  margin: 0.2rem;
  padding: 0.2rem;
  font-weight: 600;
  max-height: 95%;
  color: #333;
  border-radius: 240px 15px 100px 15px / 15px 200px 15px 185px;
  background-color: rgba(255, 255, 255);
  overflow: hidden;
  /* border: 2px solid #333; */
  opacity: 0.6;
}

.panel{
  position: relative;
  height:10rem;
  user-select: none;
  border-radius: 0.5rem;
  background-color: gray;
}

@media screen and (min-width: 576px) {
    /* sm */
  .panel {
    height:15rem;
  }
}
@media screen and (min-width: 768px) {
    /* md */
  .panel {
    height:17rem;
  }
}
@media screen and (min-width: 992px) {
    /* lg */
  .panel {
    height:17rem;
  }
}
@media screen and (min-width: 1200px) {
    /* lg */
  .panel {
    height:15rem;
  }
}
</style>
