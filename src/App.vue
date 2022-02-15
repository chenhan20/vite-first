<script setup>

import { ref } from 'vue'
const scroll = ref(false)
const total = ref(10)
const animationDuration = 10
// 只能有兩張同時做淡入淡出動畫
const active = ref(0)
const preactive = ref(0)



const img = function (n) {
  return {
    backgroundImage: `url(https://picsum.photos/1920/1200?${n})`,
    // backgroundImage: `url(/tesla_${n}.jpg)`,
    animationDuration: `${animationDuration}s`
  }
}

setInterval(function () {
  preactive.value = active.value
  active.value = (active.value + 1 + total.value) % total.value
}, animationDuration / 2 * 1000)

window.addEventListener('scroll', function () {
  scroll.value = (window.scrollY > 0)
})

</script>

<template>
  <div class="text"></div>
  <div class="kv" :class="{ scroll }">
    <ul class="kvList">
      <li
        v-for="n in total"
        :style="img(n)"
        :key="n"
        :class="{ animate: active === n - 1 || preactive === n - 1 }"
      ></li>
    </ul>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}

body {
  height: 200vh;
}

.kv {
  position: relative;
  width: 100vw;
  height: 100vh;
}
.kvList {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: 0.5s;
}
.scroll .kvList {
  width: 1200px;
  height: 300px;
}

.kvList > li {
  opacity: 0;
  position: absolute;
  width: 100%;
  height: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: 150% auto;
  list-style: none;
}
.kvList > li.animate {
  animation-name: kvAnimate;
  animation-timing-function: linear;
}

@keyframes kvAnimate {
  0% {
    opacity: 0;
    background-size: 200% auto;
  }
  25% {
    opacity: 1;
  }
  50% {
    opacity: 1;
  }
  75% {
    opacity: 0;
  }
  to {
    opacity: 0;
    background-size: 100% auto;
  }
}
</style>
