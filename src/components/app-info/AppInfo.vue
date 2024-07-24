<template>
    <div class="app-info">
        <p class="fs-3 text-uppercase">Barcha konolar soni: {{allMoviesCount}}</p>
        <p class="fs-4 text-uppercase">Ko'rilgan konolar soni: {{favouriteMoviesCount}}</p>
    </div>
</template>

<script>
export default {
    props: {
        allMoviesCount: {
            type: Number,
            required: true
        },
        favouriteMoviesCount: {
            type: Number,
            required: true
        }
    }
}
</script>

<style>
.app-info{
    padding: 1.5rem;
    border-radius: 4px;
    box-shadow: 10px 15px 15px rgba(0, 0, 0, 0.15);
    background-color: #fcfaf5;
}
</style>