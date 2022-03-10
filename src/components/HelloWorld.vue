<template>
  <div class="container" @click.self="toggleClose" v-if="display">
    <div class="modal">
      <h1>Hello World Vue II</h1>
      <p>
        Let's get this stuff.. top of the world, top of the world, top of the
        world!
      </p>
      <slot></slot>
      <slot name="form"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
    display: Boolean,
  },
  methods: {
    toggleClose() {
      this.$emit("close");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  position: absolute;
  top: 0;
  background-color:rgba(230, 230, 230, .5);
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
