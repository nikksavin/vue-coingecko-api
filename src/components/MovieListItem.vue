

<template>
    <v-hover v-slot="{ hover }">
        <v-card
                class="mx-auto"
                color="grey lighten-4"
                max-width="600"
        >
            <v-img

                    :style="posterBg"
            >
                <v-expand-transition>
                    <div
                            v-if="hover"
                            class="movie-item-content d-flex transition-fast-in-fast-out deep-purple darken-3 text-h4 v-card--reveal white--text"
                            style="height: 100%;"
                    >
                        <div class="movie-info-wrapp">
                            <span class="movie-title">{{movie.Title}}</span>
                            <span class="movie-year">{{movie.Year}}</span>
                            <div class="movie-item-controls">

                                    <v-btn
                                            color="secondary"
                                            elevation="4"
                                            large
                                            x-large
                                    >Edit</v-btn>

                                    <v-btn
                                            color="primary"
                                            elevation="4"
                                            large
                                            x-large
                                    >Remove</v-btn>

                            </div>
                        </div>
                    </div>
                </v-expand-transition>
            </v-img>
            <v-card-text
                    class="pt-0"
                    style="position: relative;"
            >
            </v-card-text>
        </v-card>
    </v-hover>
</template>







<script>
    export default {
        name: "MovieListItem",
        props: {
            movie: {
                type: Object,
                required: true
            },
        },
        computed : {
            posterBg() {
                return {
                    'background-image': `url(${this.movie.Poster})`
                };
            }
        }
    }
</script>

<style lang="scss" scoped>


    .v-card {
        position: relative;
        height: 600px;
        transition: all .2s ease-in;
    }
    .v-card:hover {
      box-shadow: 0px 5px 30px rgba(0,0,0,0.7);
    }
    .v-image {
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        width: 100%;
        height: 100%!important;
        background-repeat: no-repeat;
        background-size: cover;
      background-position: center;

    }
.movie-item-content {
  width: 100%;
  height: 100%;
}

.movie-info-wrapp {
      padding: 10px;
      position: absolute;

      width: 100%;
      height: 100%;
      display: flex;

      flex-direction: column;
    }

    .movie-item-controls {
      margin-top: auto;
    }

  .movie-item-controls button {
    width: 100%;

  }

    .movie-year {
      margin-top: 30px;
    }

    .movie-year, .movie-title {
          font-size: 1em!important;
        }
</style>