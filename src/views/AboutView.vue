<script setup lang="ts">
import { ref, computed } from 'vue';
import PagePanelVue from '@/components/PagePanel.vue';

const pageList =  ref([] as Array<string>);
pageList.value = "PAGE,PAGE2,PAGE3".split(",");

</script>

<template>
  <div class="about container">
    <h1>This is an about page</h1>
    
    <div class="row g-lg-3 g-md-2 g-1">
        <PagePanelVue
          v-for="( page , index ) in pageList"
          :key="index" :pagetitle="page"/>
    </div>
  </div>
</template>

<style>
</style>
