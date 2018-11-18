<template>
  <div id="app">
    <Home v-if="!isLogin && loaded"></Home>
    <Editor v-if="isLogin && loaded" :user="userData"></Editor>
    <Loading v-if="!loaded"></Loading>
    <!--<img src="./assets/logo.png">
    <router-view/>-->
  </div>
</template>

<script>
import Home from './components/Home.vue'
import Editor from './components/Editor.vue'
import Loading from './components/Loading.vue'

export default {
  name: 'app',
  data () {
    return {
      isLogin: false,
      userData: null,
      loaded: false
    }
  },
  beforeCreate: function () {
    firebase.auth().onAuthStateChanged(user => {
      console.log(user)
      if (user) {
        this.isLogin = true
        this.userData = user
      } else {
        this.isLogin = false
        this.userData = null
      }
      this.loaded = true
    })
  },
  components: {
    Home: Home,
    Editor: Editor,
    Loading: Loading
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
