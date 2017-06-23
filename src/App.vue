<template>
  <div id="app">
    <div class="header">
        <h1>Vue.js Poster Store</h1>
        <input type="text" v-model="searchText" placeholder="Search posters..." />
        <button @click="search">Search</button>
    </div>
    <div class="main">
        <div class="products">
            <div v-for="poster in posters">
              <img :src="poster.link" width="200px" />
            </div>
        </div>
        <div class="cart">
            <h2>Shopping Cart</h2>
            <div>
                No items in the cart.
            </div>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      searchText: '',
      posters: []
    }
  },
  methods: {
    search(){
      this.$http.get('http://localhost:3000/search/'.concat(this.searchText)).then(function(res){
        this.posters = res.data;
      })
    }
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

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
