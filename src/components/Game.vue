<template>
  <div v-if="display" class="container">
    <div @click="fire" class="modal">click me!){{ time }}</div>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";

export default {
  props: {
    time: null,
  },
  emits: ["close"],
  setup({ time }, { emit }) {
    console.log(time);
    let display = ref(false)
    const cap = ref(10000).value
    let counter = ref(0).value
    let accumulator
    
    
    function fire() {
      clearInterval(accumulator);
        display.value = false
      emit("close", counter);
    }

    function start() {
      display.value = true
      accumulator = setInterval(() => {
        if (counter >= cap) {
          fire()
        } else {
          counter += 10
        }
      }, 10)
    }

    onMounted(() => {
      console.log("game time delay: ", time);
      start();
    });

    return { display, fire };
  },
};
</script>

<style>
.container {
  position: absolute;
  top: 0;
  background-color: rgba(230, 230, 230, 0.5);
  width: 100%;
  height: 100%;
  z-index: 1;
}

.modal {
  background: tomato;
  width: 45%;
  padding: 4rem;
  margin: 10rem auto;
  z-index: 10 !important;
  opacity: 1 !important;
}
</style>
