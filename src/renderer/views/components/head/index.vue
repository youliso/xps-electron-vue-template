<template>
  <div class="head-info drag">
    <div v-if="isMacintosh" class="content">
      <div></div>
      <div class="title">{{ title }}</div>
    </div>
    <div v-else class="content">
      <div class="title">{{ title }}</div>
      <div v-if="eventShow" class="events">
        <div @click="min" class="event min no-drag"></div>
        <div @click="maxMin" class="event max-min no-drag"></div>
        <div @click="close" class="event close no-drag"></div>
      </div>
    </div>
  </div>
</template>



<script setup lang='ts' >
import { windowClose, windowMaxMin, windowMin } from '@/renderer/common/window';
import customize from '@/renderer/store/customize';

const props = defineProps({
  eventShow: {
    type: Boolean,
    default: true
  }
});

const isMacintosh = window.environment.platform === 'darwin';


let title = (customize.get() as Customize_Route).title

function min() {
  windowMin();
}

function maxMin() {
  windowMaxMin();
}

function close() {
  windowClose();
}

</script>

<style lang='scss' scoped>
@import "./scss/index";
</style>