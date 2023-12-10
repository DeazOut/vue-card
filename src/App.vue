<template>
  <HelloWorld fname = "Central" v-bind:mail="mail" lname="Cee"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return{
      mail:'',
      fname: '',
      lname:''
    }
    
  },
  methods:
  {
    getUserData(){
      this.axios.get('https://randomuser.me/api/').then((response) => {
        console.log(response.data)  
        this.mail = response.data.results[0].email // подставляем данные от сервера
      })
    }
  },
  mounted(){
    this.getUserData();
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
