<template>
    <div class="notification-black" :class="[notification ? 'opened' : '']">
        Color {{color}} copied to your clipboard
    </div>
</template>

<script>
import EventBus from '@/event-bus.js';

export default {
  data() {
    return {
      notification: false,
      notificationTimer: null,
      color: '#000000',
    };
  },
  mounted() {
    EventBus.$on('showNotification', (color) => {
      this.color = color;
      this.notification = true;

      clearTimeout(this.notificationTimer);
      this.notificationTimer = setTimeout(() => {
        this.notification = false;
        this.notificationTimer = null;
      }, 1500);
    });
  },
};
</script>

<style lang="scss">
    .notification-black {
        display: inline-block;
        padding: 10px 30px;
        background: #000;
        color: #E9E9EC;
        font-size: 12px;
        border-radius: 30px;
        position: absolute;
        top: -50px;
        left: 50%;
        transform: translate(-50%, 0);
        transition: 0.5s top ease-in-out;

        &.opened {
            top: 50px;
        }
    }
</style>
