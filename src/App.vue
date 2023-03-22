<template>
  <Header class="header" :total="total" @increaseTotal="increaseTotal"/>
  <nav>
    <router-link to="/">Home</router-link> |
  </nav> 
  <router-view/>
</template>

<script>
  import Header from './components/header/HeaderView.vue';

  export default {
  components: {
      Header
  },
  data() {
    return {
      total: undefined
    }
  },
  methods: {
    increaseTotal() {
      this.total += 1
      console.log(this.total)
    }
  },
  mounted() {
    fetch('http://localhost:3000/tasks')
      .then((res) => res.json())
      .then((data) => this.total = data.length)
  }

}
</script>
<style>


@import url('https://fonts.googleapis.com/css2?family=Basic&family=Bokor&family=Cairo:wght@200;300;400;500;600;800;900;1000&display=swap');

*{
  margin: 0;
  padding: 0;
}

body{
  background-color: rgb(88, 84, 84);
}

.stop-scrolling{
  overflow: hidden;
}
        
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  background-image: linear-gradient(225deg, #0B0B0C, #0b0b0c73);
  min-height: 100vh;
}

.header{
  padding-top: 30px;
}

h1{
  font-family: bokor, cursive;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
