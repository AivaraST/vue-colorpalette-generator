<template>
    <div class="color-grid-item" @click="copyClipboard" :data-clipboard-text="color">
        <div class="color-grid-card">
            <div class="color-grid-visuals" :style="{background: color}"></div>
            <span class="color-grid-hex-value">{{color}}</span>
        </div>
    </div>
</template>

<script>
import ClipboardJS from 'clipboard';
import EventBus from '@/event-bus.js';

const clipboard = new ClipboardJS('.color-grid-item');

clipboard.on('success', (e) => {
  e.clearSelection();
});

export default {
  props: {
    color: {
      type: String,
    },
  },
  methods: {
    copyClipboard() {
      EventBus.$emit('showNotification', this.color);
    },
  },
};
</script>

<style lang="scss">
    .color-grid-item {
        padding: 10px 10px;
        width: 20%;
        transition: 0.5s transform ease-in-out;

        &:hover {
            transform: translate(0, -10px);
        }
    }

    .color-grid-card {
        background-color: #FFFFFF;
        padding: 10px 10px 0 10px;
        border-radius: 15px;
        cursor: pointer;
    }

    .color-grid-visuals {
        background: #000;
        width: 100%;
        height: 250px;
        border-radius: 5px;
    }

    .color-grid-hex-value {
        font-size: 12px;
        color: #0C1226;
        display: block;
        text-align: center;
        padding: 10px 0;
    }

    @media only screen and (max-width: 968px) {
      .color-grid-item {
        width: 50%;
      }
    }

    @media only screen and (max-width: 768px) {
      .color-grid-item {
        width: 100%;
      }
    }
</style>
