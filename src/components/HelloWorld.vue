<template>
  <div id="app">
    <h1>IMDB movies:</h1>
    <div class="nav">
        <button>Lowest rated</button>
        <button>Highest rated</button>
    </div>
    <ul>
        <li>
            Movie name <span>Movie rating</span>
        </li>
    </ul>
    {{info}}
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      info: null,
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted () {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response))
  },
  methods: {
    getColorByScore (score) {
      switch (score) {
        case 8:
          return '#2196f3'
        default:
          break
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
