<template>
  <div class="flex py-2 mt-0.5 border-b border-black border-opacity-10 dark:border-litepie-secondary-700 dark:border-opacity-100">
    <div
      v-for="(day, keyDay) in weeks"
      :key="keyDay"
      :style="{
        width: `calc(100% / ${weeks.length})`
      }"
      class="text-litepie-secondary-500 text-xs 2xl:text-sm tracking-wide font-medium text-center cursor-default dark:text-litepie-secondary-400"
    >
      <span v-text="day"> </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LitepieWeek',
  props: {
    weeks: Array
  },
  inheritAttrs: false
};
</script>
