<template>
  <v-container>
    <h3 class="v-list-item__title">IMDB Top 250</h3>
    <v-row
        no-gutters>
      <template v-if="isExist">
        <v-col
            v-for="(movie, key) in list"
            :key="key"
        >

        </v-col>
      </template>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: "MoviesList",
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
  }
</script>

<style scoped>
  .v-list-item__title {
    font-size: 50px;
    margin-bottom: 30px;
  }
</style>