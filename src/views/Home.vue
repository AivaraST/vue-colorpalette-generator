<template>
  <div class="home-page">
      <div class="container">
        <GlobalEvent @keydown.space.prevent="regeneratePalette"></GlobalEvent>
        <NotificationCopied></NotificationCopied>
        <PaletteGrid :colors="colors"></PaletteGrid>
        <RegenerateButton @click.native="regeneratePalette"></RegenerateButton>
        <span class="btn-instructions">Or just press the "Spacebar" to generate new palettes.</span>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ColorScheme from 'color-scheme';
import GlobalEvent from 'vue-global-events';
import NotificationCopied from '@/components/NotificationCopied.vue';
import PaletteGrid from '@/components/PaletteGrid.vue';
import RegenerateButton from '@/components/RegenerateButton.vue';

export default {
  name: 'Home',
  data() {
    return {
      colors: ['#EEEDF0', '#A1B5C1', '#F9ACA7', '#68747D', '#CF365F'],
    };
  },
  methods: {
    regeneratePalette() {
      const variations = [
        'pastel',
        'soft',
        'light',
        'pale',
      ];

      const scheme = new ColorScheme();
      const randomHue = Math.floor(Math.random() * 100000000) + 1;
      const randomColors = scheme.from_hue(randomHue).scheme('analogic').variation(variations[Math.floor(Math.random() * variations.length)])
        .distance(Math.random())
        .colors();

      this.colors.forEach((color, index) => {
        this.$set(this.colors, index, `#${randomColors[index]}`);
      });
    },
  },
  created() {
    this.regeneratePalette();
  },
  components: {
    GlobalEvent,
    NotificationCopied,
    PaletteGrid,
    RegenerateButton,
  },
};
</script>

<style lang="scss">
  .btn-instructions {
    display: block;
    text-align: center;
    color: #000;
    font-size: 12px;
    font-weight: 200;
    margin-top: 15px;
    margin-bottom: 75px;
  }

  h1 {
    font-weight: 400;
    color: #0C1226;
    text-align: center;
  }
</style>
