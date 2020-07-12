<template>
    <div class="color-grid">
      <PalleteGridItem
      v-for="color in colors"
      :key="color"
      :color="color">
      </PalleteGridItem>
    </div>
</template>

<script>
import PalleteGridItem from './PalleteGridItem.vue';

export default {
  props: ['colors'],
  components: {
    PalleteGridItem,
  },
  methods: {
    lmoa() {
      return console.log(this.colors);
    },
  },
};
</script>

<style>
    .color-grid {
        padding: 100px 0;
        display: flex;
    }
</style>
