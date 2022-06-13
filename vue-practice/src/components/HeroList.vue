<template>

  <div id="container">
    <input type="text" placeholder="Enter a hero here" v-model="newHero" />
    <button type="submit" v-on:click="onClick" > Add Hero </button>

    <ul>
      <li v-for="hero in heroes" :key="hero.name">
        {{hero.name}}
      </li>
    </ul>

    <input type="text" placeholder="Who's getting removed?" v-model="heroToRemove" />
    <button type="submit" v-on:click="removeHero" > Remove Hero </button>

    <p v-if="showMessageToUser">{{messageToUser}}</p>
  </div>


</template>

<script>
export default {
  name: "HeroList",
  props: {
    providedList: {
      type:Array,
      // required:true,
      // validator(value) {
      //   return ['open', 'filled', 'half'].includes(value);
      // },
    }
  },
  data: function (){
    return {
      newHero: '',
      heroToRemove: '',
      heroes: this.providedList,
      messageToUser:'',
      showMessageToUser: false
    }
  },
  methods:{
    onClick: function () {
      this.heroes.push({name:this.newHero})
      this.newHero =''
    },
    removeHero: function () {
      // get array with that hero removed
      const newList = this.heroes.filter((hero) =>{

        return hero.name != this.heroToRemove
      })

      if (newList.length === this.heroes.length){
        this.messageToUser = `Couldn't find the hero ${this.heroToRemove}, type it EXACTLY including spaces`
        this.showMessageToUser=true
        this.heroToRemove=''
        return
      } else {
        this.messageToUser = `Removed ${this.heroToRemove} from List!`
        this.showMessageToUser=true
        this.heroes = [...newList]
      }

      this.heroToRemove =''

    }
  }
}
</script>

<style scoped>
  #container {
    max-width: 800px;
    margin: 0 auto;
  }

  #container ul {
    list-style: none;
  }
</style>