<template>
  <div class="top-bar">
      <div class="time">
          9:41
      </div>
      <div class="status">
          <SignalIcon />
          <WifiIcon />
          <BatteryIcon />
      </div>
  </div>
</template>

<script>
import WifiIcon from 'vue-material-design-icons/Wifi';
import SignalIcon from 'vue-material-design-icons/Signal';
import BatteryIcon from 'vue-material-design-icons/Battery';
export default {
    name: 'top-status-bar',
    components: {
        WifiIcon,
        SignalIcon,
        BatteryIcon
    }
}
</script>

<style scoped>
    .top-bar {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        z-index: 9000;
    }
    .top-bar .time {
        float: left;
        color: #fff;
        margin-top: 20px;
        margin-left: 20px;
        font-size: 0.8rem;
    }
    .status {
        float: right;
        color: #fff;
        margin-right: 20px;
        margin-top: 20px;
        font-size: 0.8rem;
    }
    .status * {
        padding: 3px;
    }
</style>