

<script setup>
import { ref, nextTick } from "vue";

const count = ref(0);
const counter = ref(null);

function increment() {
  count.value++;

  /**
   * DOM is not yet updated, how can we make sure that the DOM gets updated
   * Make the output be true
   *   
   * nextTick是Vue.js中的一个方法，它可以让你在下一次DOM更新后执行一些代码。这样可以确保你的代码和DOM的状态是同步的，避免出现一些错误或不一致的情况。👍

nextTick的一些常见的使用场景有：

当你想要使用setTimeout来延迟一些操作，但是不确定延迟的时间是否合适，你可以使用nextTick来替代，它会在最合适的时机执行你的代码。
当你想要在数据变化后对DOM进行一些操作或检查，比如获取元素的高度、宽度、位置等，你可以使用nextTick来保证DOM已经更新，然后再获取正确的值。
当你在进行一些异步的数据加载或处理，比如从API获取数据，你可以使用nextTick来等待数据加载完成，然后再更新视图或执行其他逻辑。
  */

  nextTick(() => {
    // +一元运算符, 将字符串转换为数字
    console.log(+counter.value.textContent === 1);
  });
}
</script>

<template>
  <button ref="counter" @click="increment">
    {{ count }}
  </button>
</template>
