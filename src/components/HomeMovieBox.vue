<template>
  <div class="homeMovieBox">
    <img :src="movieInfo.Poster" alt="" class="poster">
    <div class="desc">
      <div class="title">{{ movieInfo.Title }}</div>
      <div class="year">{{ movieInfo.Year }}</div>
      <div class="type">{{ movieInfo.Type }}</div>
<!--      <div class="imdbID">{{ movieInfo.imdbID }}</div>-->
    </div>
  </div>
</template>

<script>
import {ref} from "vue";

export default {
  name: "HomeMovieBox",
  props: ['allAboutThisMovie'],
  setup(props) {
    const movieInfo = ref(props.allAboutThisMovie)
    return {
      movieInfo
    }
  }
}
</script>

<style lang="scss" scoped>
.homeMovieBox {
  display: flex;
  width: 100%;
  height: 115px;
  font-size: 12px;
  background: #ffffff;
  box-shadow:  13px 13px 26px #c9c9c9,
  -13px -13px 26px #ffffff;
  border-radius: 15px;
  padding: 10px;
  margin: 10px 0;

  img {
    width: 60px;
    border-radius: 10px;
  }

  .desc {
    flex: 1;
    padding-left: 10px;
    position: relative;

    .title {
      font-size: 20px;
      font-weight: bold;
    }

    .year {
      font-size: 18px;
      font-weight: bold;
      color: #7e0000;
      margin-top: 10px;
      position: absolute;
      bottom: 0;
      padding: 4px 0;
    }

    .type {
      font-size: 16px;
      font-weight: bold;
      color: white;
      background-color: #575757;
      padding: 5px 10px;
      border-radius: 12px;
      position: absolute;
      bottom: 0;
      right: 0;
    }
  }
}
</style>
