<template>
    <div class="back"> </div>
    <button class="arrowButton sideArrow01" @click="getData()">Get joke</button>
    <jokeDiv :joke_first=first :joke_second=second />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import jokeDiv from './components/getJokes.vue'
import axios from "axios"

export default {
  name: 'App',
  data(){
    return{
        first: "",
        second: ""
    }
  },
  components: {
    jokeDiv
  },

  methods: {
    async getData(){
      const url="https://v2.jokeapi.dev/joke/Any?safe-mode"
      const response = await axios.get(url)
      //const results = response.data.results
      const type = response["data"]["type"]
      console.log(response["data"])
      if (type == "single"){
        this.first = response["data"]["joke"]
        this.second = ""
      }else{
         this.first = response["data"]["setup"]
         this.second = response["data"]["delivery"]
      }

    }
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: content-box;
  }

body{
  background: #25577a;
  overflow: hidden;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.back{
  position: absolute;
  inset: 0;
  max-width: 100vw;
  max-height: 98vh;
  background: url("@/assets/smiley.svg") no-repeat no-repeat;
  transform: scale(2) translateX(20vh);
  opacity: .03;
  z-index: -100;
  overflow: hidden;
}

.arrowButton {
  text-align: center;
  display: inline-block;
  position: relative;
  text-decoration: none;
  color: #FFFFFF;
  text-transform: capitalize;
  font-family: Roboto, sans-serif;
  font-size: 1.3em;
  padding: 20px 0px;
  margin-bottom: 3rem;
  width: 150px;
  height: 1em;
  border-radius: 50px;
  overflow: hidden;
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.5);
  transition: all 0.2s linear 0s;
}

.sideArrow01 {
  background-color: rgb(79, 1, 168);
}
.sideArrow01:before {
  content: ">";
  font-family: FontAwesome;
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  top: 0;
  left: 0px;
  height: 100%;
  width: 30px;
  background-color: rgb(107, 85, 133);
  opacity: 1;
  border-radius: 0 50% 50% 0;
  transform: scale(0, 1);
  transform-origin: left center;
  transition: all 0.2s linear 0s;
}
.sideArrow01:hover {
  text-indent: 30px;
}
.sideArrow01:hover:before {
  transform: scale(1, 1);
  text-indent: 0;
}
</style>
