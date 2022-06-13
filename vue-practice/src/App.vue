<template>
  <div id="app">
    <GreetingUser name="Alex"/>
    <HeroList :providedList="myList"/>
  </div>
</template>

<script>
import GreetingUser from "@/components/GreetingUser";
import HeroList from "@/components/HeroList";


export default {
  name: 'App',
  components: {
    GreetingUser,
    HeroList
  },
  data: function (){
   return {
     myList : [
       { name: 'Superman'},
       { name: 'Batman'},
       { name: 'The Flash'},
       { name: 'Green Lantern'}
     ]}
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
