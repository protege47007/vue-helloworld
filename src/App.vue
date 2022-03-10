<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" @click="toggleClose"/>
    <HelloWorld msg="Welcome to Your Vue.js App" :display="display" @close="toggleClose">
      <template v-slot:form>
      <form ref="form" @submit="form">
        <input type="text" ref="name" placeholder="name">
        <br>
        <input type="text" ref="post" placeholder="Position">
        <br>
        <input type="number" ref="xp" placeholder="years of experience">
        <br>
        <button type="submit">Post</button>
      </form>
      </template>
      <h3>Name: {{nom}}</h3>
      <h3>Vote for your next: {{position}}</h3>
      <h4>He has {{xyz}} years of experience</h4>
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data: () => ({
    nom: 'John Doe',
    position: 'Janitor',
    xyz: 999,
    display: false,

  }),
  methods: {
    form(e){
      e.preventDefault();
      this.nom = this.$refs.name.value
      this.position = this.$refs.post.value
      this.xyz = this.$refs.xp.value
    },
    
    toggleClose(){
      this.display = !this.display
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
