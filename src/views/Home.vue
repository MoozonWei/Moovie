<template>
  <div class="home">
    <form @submit.prevent="searchMovies" class="search-from">
      <input type="text" class="searchBar" placeholder="What are you looking for?" v-model="search">
      <input type="submit" class="searchBtn" value="Search">
    </form>

    <div class="searchResultBox">
      <HomeMovieBox
          v-for="item in movies"
          :key="item.imdbID"
          :allAboutThisMovie="item"
      ></HomeMovieBox>
    </div>
  </div>
</template>

<script>
import {ref} from "vue";
import env from "@/env"

import HomeMovieBox from "@/components/HomeMovieBox";

export default {
  name: 'Home',
  components: {HomeMovieBox},
  setup() {
    const search = ref("")
    const movies = ref([])

    const searchMovies = () => {
      if (search.value !== "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
            .then(response => response.json())
            .then(data => {
              movies.value = data.Search
            })
      } else {
        movies.value = []
      }
    }

    return {
      search,
      movies,
      searchMovies
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  padding: 0 20px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  overflow-y: scroll;

  form {
    width: 100%;
    display: flex;
    justify-content: space-around;

    .searchBar {
      flex: 1;
      padding: 0 15px;
      font-size: 20px;
      border-radius: 15px 0 0 15px;
      background: #ffffff;
      box-shadow:  11px 11px 18px #e0e0e0,
      -11px -11px 18px #ffffff;
      line-height: 2.5em;

      &::placeholder {
        color: #cecece;
      }
    }

    .searchBtn {
      border-radius: 0 15px 15px 0;
      padding: 0 10px;
      font-size: 20px;
      font-weight: bold;
      background-color: #ffc12b;
      box-shadow:  11px 11px 18px #e0e0e0,
      -11px -11px 18px #ffffff;
      line-height: 2.5em;
    }
  }

  .searchResultBox {
    margin-top: 16px;
    display: flex;
    align-items: normal;
    justify-content: space-between;
    flex-wrap: wrap;
  }
}
</style>
