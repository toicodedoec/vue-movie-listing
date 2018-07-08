<template>
  <div id="app">
    <h1>IMDB movies:</h1>
    <div class="nav">
        <button @click="sort('asc')">Lowest rated</button>
        <button @click="sort('desc')">Highest rated</button>
    </div>
    <ul>
        <li>
            Movie name <span>Movie rating</span>
        </li>
        <li v-for="m in movies" :key="m.name" :style="{'background-color': getColorByRating(m.rating)}">
            {{m.name}} <span>{{m.rating}}</span>
        </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      movies: [],
      mockMovieNames: [
        {rating: 6.1, name: 'Blade Runner 2049'},
        {rating: 8.5, name: 'Logan'},
        {rating: 7.3, name: 'Star Wars: The Last Jedi'},
        {rating: 5.2, name: 'Three Billboards Outside Ebbing, Missouri'},
        {rating: 7.5, name: 'War for the Planet of the Apes'},
        {rating: 4.0, name: 'Dunkirk'},
        {rating: 8, name: 'Baby Driver'},
        {rating: 7.7, name: 'Spider-Man: Homecoming'},
        {rating: 9.4, name: 'IT'},
        {rating: 7.5, name: 'The Disaster Artist'},
        {rating: 7.5, name: 'Wonder Woman'},
        {rating: 8.7, name: 'Get Out'},
        {rating: 7.9, name: 'Thor: Ragnarok'},
        {rating: 8.5, name: 'Coco'},
        {rating: 5.5, name: 'I, Tonya'}
      ]
    }
  },
  mounted () {
    axios
      .get('http://www.omdbapi.com/?i=tt3896198&apikey=8c92544d')
      .then(response => {
        // get mock data to fill full of 15 records
        this.movies = this.mockMovieNames
        // sort by rating
        this.movies = this.sort('asc')
      })
  },
  methods: {
    getColorByRating (rating) {
      return `rgba(55,185,134,${rating/10})`
    },
    sort (ordering) {
      return this.movies.sort((a, b) => ordering === 'asc' ? a.rating - b.rating : b.rating - a.rating)
    }
  }
}
</script>
