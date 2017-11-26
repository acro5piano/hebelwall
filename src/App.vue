<template>
  <div id="app">
    <div class="wrap">
      <div class="vertical-center">
        <transition name="zoom-out">
          <div class="logo" v-if="time < 1000">
            hebel
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      time: 0,
    }
  },
  mounted () {
    setInterval(() => {
      this.time += 100
    }, 100)
  },
  methods: {
    passedSecond (ms) {
      return ms < this.time
    }
  }
}
</script>

<style>
body {
  font-family: 'PT Sans', sans-serif;
}
.wrap {
  background: #b73b1b;
  height: 100vh;
  overflow: hidden;
}

.vertical-center {
  padding-top: 50vh;
}
.logo {
  text-align: center;
  font-size: 72px;
  font-weight: bold;
}

.zoom-out-leave-active {
  animation: zoom-then-move .5s reverse;
}
@keyframes zoom-then-move {
  0% {
    transform: scale(0.9);
  }
  50% {
    margin-left: 100%;
    font-size: 90px;
    opacity: 0;
  }
}
</style>
