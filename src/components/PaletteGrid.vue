<template>
    <div class="color-grid">
      <PalleteGridItem
      v-for="(color, index) in colors"
      :key="index"
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
};
</script>

<style lang="scss">
    .color-grid {
        display: flex;
        flex-wrap: wrap;
        margin-bottom: 50px;
    }
</style>
