<template>
  <div class="movie-add-form">
    <h3>Yangi kino qo'shish</h3>
    <form class="add-form d-flex" @submit.prevent="addMovie">
      <input 
        type="text" 
        class="form-control new-movie-label" 
        placeholder="Qanday kino?" 
        v-model="name">
      <input 
        type="number" 
        class="form-control new-movie-label" 
        placeholder="Nechi marotaba ko'rilgan" 
        v-model.number="viewers">
      <button 
        class="btn btn-outline-dark" 
        type="submit">Qo'shish</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      viewers: "", 
    };
  },
  methods: {
    addMovie() {
      const newMovie = {
        name: this.name,
        viewers: this.viewers,
        favourite: false,
        like: false,
        id: Date.now() 
      };
      
      this.$emit('createMovie', newMovie);
      this.name = ""; 
      this.viewers = ""; 
    }
  }
};
</script>



<style>
.movie-add-form {
  margin-bottom: 1rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>