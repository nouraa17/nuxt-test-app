<template>
  <div>
    <SearchJokes @search-text="searchText"></SearchJokes>
    <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"></Joke>
  </div>
</template>

<script>
import axios from 'axios';
import Joke from "../../components/Joke.vue";
import SearchJokes from "../../components/SearchJokes.vue";
export default {
  name: "index",
  components:{
    Joke,
    SearchJokes,
  },
  data(){
    return{
      jokes:[],
    }
  },
  async created() {
    const config = {
      headers : {
        'Accept': 'application/json',
      }
    }
    try {
      const res = await axios.get('https://icanhazdadjoke.com/search',config)
      // console.log(res.data)
      this.jokes= res.data.results;
    }
    catch (error){
      console.log(error)
    }
  },
  head(){
    return{
      title:'Dad Jokes',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  },
  methods:{
    async searchText(text){
      const config = {
        headers : {
          'Accept': 'application/json',
        }
      }
      try {
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config)
        // console.log(res.data)
        this.jokes= res.data.results;
      }
      catch (error){
        console.log(error)
      }

    }
  }
}
</script>


<style scoped>

</style>
