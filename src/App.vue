<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <div id="testBtn" @mousedown="handleMouseDown">testsetsetets </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import {ipcRenderer} from 'electron'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup() {
    const handleMouseDown = () => {
      console.log('ipcRenderer', ipcRenderer)
      ipcRenderer.send('testFS','sucess!!!')
      ipcRenderer.on('reciveFS', (evt, payload) => {
        console.log('recive!!!', evt, payload)
      })
    }

    return {
      handleMouseDown
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
</style>
