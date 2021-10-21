<template>
  <div id="app">

    <v-app>
      <v-main>
          <PosterBg :poster="posterBg" />
          <MoviesList :list="moviesList" @changePoster="onChangePoster"/>
      </v-main>
    </v-app>

  </div>
</template>

<script>
import {mapActions, mapGetters} from 'vuex';
import MoviesList from "@/components/MoviesList";
import PosterBg from "@/components/PosterBg";

export default {
  name: 'App',
    data: () => ({
        posterBg: "",
    }),

  components: {
    MoviesList,
      PosterBg,
  },
  computed: {
    ...mapGetters('movies', ["moviesList"])
  } ,
  methods: {
    ...mapActions("movies", ["fetchMovies"]),
      onChangePoster(poster) {
        this.posterBg = poster;
      }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
}
v-main {
  position: relative;
}
</style>
