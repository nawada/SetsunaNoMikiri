<template>
  <div id="app">
    <SetsunaStart v-if="shownStart" @clickStart="start" :records="records"></SetsunaStart>
    <SetsunaWait v-else-if="shownWait"></SetsunaWait>
    <SetsunaAction v-else-if="shownAction"></SetsunaAction>
    <SetsunaEnd v-else @endNextEvent="showStart" :tickTime="tickTime"></SetsunaEnd>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import SetsunaStart from './components/SetsunaStart.vue';
import SetsunaWait from './components/SetsunaWait.vue';
import SetsunaAction from './components/SetsunaAction.vue';
import SetsunaEnd from './components/SetsunaEnd.vue';

export default {
  name: 'app',
  data: function () {
    return {
      shownStart: false,
      shownWait: false,
      shownAction: false,
      shownEnd: false,
      tickStartTime: 0,
      tickTime: 0,
      records: [],
    };
  },
  components: {
    SetsunaStart,
    SetsunaWait,
    SetsunaAction,
    SetsunaEnd,
  },
  created: function () {
    this.shownStart = true;
  },
  mounted: function () {
    const that = this;

    window.addEventListener('keypress', function (e) {
      const keyCode = e.keyCode;
      that.pressedKeyCode = keyCode;

      if(that.shownStart && (keyCode === 13 || keyCode === 32)) {
        // when shown Start child vue and pressed ENTER key
        that.start();
      } else if(that.shownAction && (keyCode === 13 || keyCode === 32)) {
        // when shown Action child vue and pressed SPACE key
        that.tickTime = (+new Date()) - that.tickStartTime;
        that.showEnd();
      } else if(that.shownEnd && (keyCode === 13 || keyCode === 32)) {
        // when shown End child vue and pressed ENTER or SPACE keys
        that.end();
      }
    });
  },
  methods: {
    showStart: function () {
      this.shownStart = true;
      this.shownWait = false;
      this.shownAction = false;
      this.shownEnd = false;
    },
    showWait: function () {
      this.shownStart = false;
      this.shownWait = true;
      this.shownAction = false;
      this.shownEnd = false;
    },
    showAction: function () {
      this.shownStart = false;
      this.shownWait = false;
      this.shownAction = true;
      this.shownEnd = false;
    },
    showEnd: function () {
      this.shownStart = false;
      this.shownWait = false;
      this.shownAction = false;
      this.shownEnd = true;
    },
    start: function () {
      this.showWait();
      this.waitForAction();
    },
    waitForAction: function () {
      const waitTime =  5000 + (Math.random() * 3000);
      const that = this;
      setTimeout(function() {
        that.tickStartTime = +new Date()
        that.showAction();
      }, waitTime);
    },
    end: function () {
      this.records.push(this.tickTime);
      this.showStart();
    },
  }
};
</script>

<style lang="scss">
.center {
  text-align: center;
}

.bigger-font {
  font-size: 200%;
  font-weight: bold;
}

.biggest-font {
  font-size: 300%;
  font-weight: bold;
}

.red {
    color: #ff0000;
}
</style>
