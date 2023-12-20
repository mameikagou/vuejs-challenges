<script setup lang="ts">
import { onMounted, inject, onUnmounted} from "vue"

const timer = inject("timer")
const count = inject("count")

// 计时器因为没有被销毁, 所以, 无法正常运转; 
onMounted(() => {
  timer.value = window.setInterval(() => {
    count.value++
  }, 1000)
})

// 离开的时候销毁
onUnmounted(() => {
  window.clearInterval(timer.value)
})
</script>

<template>
  <div>
    <p>
      Child Component: {{ count }}
    </p>
  </div>
</template>
