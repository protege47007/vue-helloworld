<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" @click="toggleClose"/>
    <HelloWorld msg="Welcome to Your Vue.js App" :display="display" :time="time" @close="toggleClose">
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
    <button @click="startGame">Play Game</button>
    <div v-if="mountModal">
      <Game :time="time" @close="endGame" />
    </div>
    
    <Result v-if="score" :score="score" @closeResult="closeResult" />
    <Form/>
  </div>
</template>

<script>

import HelloWorld from "./components/HelloWorld.vue";
import Result from './components/Result.vue';
import Game from "./components/Game.vue"
import Form from './components/Form.vue';

export default {
  name: "App",
  components: {
    HelloWorld,
    Game,
    Result,
    Form,
    
  },
  data: () => ({
    nom: 'John Doe',
    position: 'Janitor',
    xyz: 999,
    display: false,
    mountModal: false,
    score: null,
    time: 0

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
    },

    startGame(){
      this.time = 2000 + Math.random() * 5000
      this.mountModal = true
      this.score = null
    },

    endGame(val){
      console.log('app end fired', val);
      this.score = val
      this.mountModal = false
      
    },

    closeResult(){
      this.score = ""
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
