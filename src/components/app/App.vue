<template>
  <div class="app font-monospace">
    <div class="content">
      <app-info-vue :allMoviesCount="movies.length" :favouriteMoviesCount="movies.filter(movie => movie.favourite).length" />
      <div class="search-panel">
        <search-panel :updateTermHandler="updateTermHandler"/>
        <app-filter-vue />
      </div>
      <movie-list :movies="onSearchHandler(movies, term)" @onToggle="onToggleHandler" @onRemove="onRemoveHandler"/>
      <movie-add-form @createMovie="createMovie" />
    </div>
  </div>
</template>

<script>
import AppFilterVue from '../appFilter/AppFilter.vue';
import AppInfoVue from '../app-info/AppInfo.vue';
import SearchPanel from '../search-panel/SearchPanel.vue';
import MovieList from '../movie-list/MovieList.vue';
import MovieAddForm from '../movie-add-form/MovieAddForm.vue';

export default {
  components: {
    AppInfoVue,
    SearchPanel,
    AppFilterVue,
    MovieList,
    MovieAddForm,
  },
  data() {
    return {
      movies: [
        {
          name: 'Omar',
          viewers: 811,
          favourite: false,
          like: true,
          id: 1,
        },
        {
          name: 'Empire of Osman',
          viewers: 411,
          favourite: false,
          like: false,
          id: 2,
        },
        {
          name: 'Ertugrul',
          viewers: 711,
          favourite: true,
          like: false,
          id: 3,
        },
      ],
      term: '',
    };
  },
  methods: {
    createMovie(item) {
      this.movies.push(item);
    },
    onToggleHandler(id, prop) {
    this.movies = this.movies.map(item => {
      if (item.id == id) {
        return {...item, [prop]: !item[prop]}
      }
      return item
    })
   },
   onRemoveHandler(id){
    this.movies = this.movies.filter(c => c.id !== id)
   },
   onSearchHandler(arr, term){
    if (term.length == 0) {
      return arr
    } 
    return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
   },
   updateTermHandler(term){
     this.term = term
   }
  },
}
</script>


<style>
.app{
  height: 100vh;
  color: #000;
}
.content{
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}
.search-panel{
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>