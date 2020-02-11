<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div class="container">
      <h2>These are my skills</h2>
      <button class="btn btn-primary btn-lg my-2" @click="adva()">ADVANCED</button>
      <div v-if="advancedlist.length>0">
        <Advanced v-for="(item, i) in advancedlist" :key="i" :ant="item"/>
      </div>
      <button class="btn btn-primary btn-lg my-2" @click="inter()">INTERMEDIATE</button>
      <div v-if="intermediatelist.length>0">
        <Intermediate v-for="(item, i) in intermediatelist" :key="i" :int="item"/>
      </div>
      <button class="btn btn-success btn-lg my-2" @click="res()">HOME</button>
    </div>

  </div>
</template>

<script>
import Intermediate from './components/HelloWorld.vue';
import Advanced from './components/Advanced.vue'

export default {
  name: 'App',
  components: {Intermediate, Advanced},
  methods: {
    adva() {
        this.skills.forEach(sk => {
          if (sk.level=="advanced") {

            this.advancedlist.push(sk.title);
            
          }
        });
    },
    inter() {
        this.skills.forEach(sk => {
          if (sk.level=="intermediate") {

            this.intermediatelist.push(sk.title);
           
          }
        });
    },
    res() {this.intermediatelist=[];
            this.advancedlist= [];}
  },
  
  data() {
    return {
      skills: [{
        title: 'javascript',
        level: 'advanced' 
      },
      {
        title: 'HTML',
        level: 'advanced' 
      },
      {
        title: 'CSS',
        level: 'intermediate' 
      },
      {
        title: 'Vue',
        level: 'intermediate' 
      }],

      advancedlist: [],
      intermediatelist : []
    }
  }
}
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
.container {display:flex;
  flex-direction: column;
  align-items:center;}

ul {padding-left: 0;}

ul li {list-style-type:disc;
  margin-left: 0;
  display: flex;
  flex-direction: column;
  align-items: flex-start;}
</style>
