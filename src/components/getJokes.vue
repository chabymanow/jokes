<template>
    <div class="jokesDiv">
        <h1>This is the jokes place</h1>
        <p>{{ joke_first}}</p>
        <p>{{ joke_second}}</p>
    </div>
</template>

<script>
export default {
  name: 'jokeDiv',
  props: {
    joke_first: String,
    joke_second: String
  }
}
</script>

<style scoped>
  .jokesDiv{
    width: 40vw;
    background: #74bbe6;
    border-radius: 20px;
    padding: 1rem;
    box-shadow: 0 0 15px rgba(0, 0, 0, .5), 0 0 5px rgba(0, 0, 0, .8);
  }

  h1{
    font-size: 1.5rem;
  }

  p{
    font-size: 1.2rem;
    margin: 1rem 1rem;
  }
</style>