<template>
  <div id="app">
    <aside v-if="showSideBar">Ma sidebar</aside>
    <p v-else>Ce qui va s'affichier si c'est false</p>

    <h2 class="title">{{msg}} {{score}}</h2>
    <input type="checkbox" v-model="isBG">
    <p v-if="isBG">Je suis un bg</p>
    <p v-else>Je ne suis pas un bg</p>
    <input type="text" v-model="firstname">
    <input type="text" v-model="lastname">


    Nom: {{lastname}}
    Prénom: {{firstname}}

    <h3 @click="clickMe">Cliquez-moi!</h3>

    <button @click="incrementScore">Cliqué {{score}} fois</button>

    <div>
      <input type="text" v-model="newTask">
      <button @click="addTask">Ajouter une tâche</button>
    </div>
    <Player />
    <Player />
    <ol>
      <li :key="task.id" v-for="task in tasks">
        {{task.content}}
      </li>
    </ol>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
import Player from './components/Player.vue';

export default {
  name: 'App',
  components: {
    Player
  },
  methods: {
    clickMe: function() {
      console.log("Je me suis fais cliquer")
    },
    incrementScore: function() {
      this.score++;
    },
    addTask: function() {
      let currTask = {
        id: uuidv4(),
        content: this.newTask};
      this.tasks.push(currTask);
    }
  },
  data: function() {
    return {msg: "Vous avez cliqué: ",
    score: 0,
    firstname: "",
    lastname:"",
    showSideBar: true,
    isBG: true,
    tasks: [
      {id: 1, content: "fffafafafafaf"},
      {id: 2, content: "azerazerazerazer"}
    ],
    newTask: [

    ]
  }
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.title {
  color: red;
}
</style>