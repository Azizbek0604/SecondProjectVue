<template>
  <ul class="movie-list movie-group">  
    <movie-list-item 
      v-for="(movie, index) in movies" 
      :key="index" 
      :movie="movie" 
      @onLike="handleLike"
    />
  </ul>
</template>

<script>
import MovieListItem from '../movie-list-item/MovieListItem.vue';

export default {
  components: {
    MovieListItem
  },
  props: {
    movies: {
      type: Array,
      required: true
    }
  },
  methods: {
    handleLike(movieId) {
      // Emit 'onLike' event with the movie ID
      this.$emit('onLike', movieId);
    }
  }
};
</script>


<style scoped>
.movie-list{
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>