<template>
  <v-container>

    <v-row>
    <h3 class="v-list-item__title">IMDBs Top 250</h3>
      <template v-if="isExist">
        <v-col
            cols="3"
            v-for="(movie, key) in list"
            :key="key"
        >
            <MovieListItem :movie="movie"  @mouseover.Native="onMouseOver(movie.Poster)" />
        </v-col>
      </template>
        <template v-else>
            <div>Empty list</div>
        </template>
    </v-row>
  </v-container>
</template>

<script>
import MovieListItem from "./MovieListItem";

  export default {
    name: "MoviesList",
      components: {
          MovieListItem,
      },
    props: {
      list: {
        type: Object,
        default: () => ({})
      }
    },
    computed: {
      isExist () {
        return Boolean(Object.keys(this.list).length);
      }
    },
    methods: {
        onMouseOver (poster) {
            this.$emit("changePoster", poster);
        }
    }
  }
</script>

<style scoped>
  .v-list-item__title {
    font-size: 50px;
    margin-bottom: 30px;
      z-index: 1;
      color: #fff;
      margin-top: 30px;
  }
</style>