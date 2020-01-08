<template>
  <div id="app">
    <h1 v-if="count % 2 === 0">{{title}}</h1>
    <h2>{{msg}}</h2>
    <h3>{{combine}}</h3>
    <button @click="add">add</button>
    <input v-model="msg"/> 
    <HelloWorld :msg="msg">
      <!-- {{user}} -->
      <template  v-slot="user">
        <div>{{user.innerMsg}}</div>
        <div>这是一个slot</div>
      </template>
    </HelloWorld>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  props: ['title'],
  components: {
    HelloWorld
  },
  watch: {
      msg(newVal, oldVal){
          if(newVal !== oldVal){
            document.title=newVal;
          }
      }
  },
  data() {
    return{
        msg: 'Vue',
        count: 0
    };
  },
  computed: {
    combine(){
      return this.title + this.msg;
    }
  },
  methods: {
    add(){
        return this.msg + this.count;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
