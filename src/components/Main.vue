<template>
  <b-container class="bv-example-row main">
    <b-row>
      <b-col cols="8">
        <video id="player" controls="controls" width="640px" height="480">
          <source :src="currentMovie.source" type="video/mp4">
        </video>
      </b-col>
      <b-col cols="4">
        <List></List>
      </b-col>
    </b-row>
  </b-container>
</template>
<script>

import DATA from '../assets/data'
import List from "./ProcedureList";

let movie = DATA[2]

export default {
  name: 'Main',
  components: {
    List
  },

  data() {
    return {
      title: '',
      movieList: DATA,
      recommendList: [DATA[2], DATA[4], DATA[1], DATA[0]],
      currentMovie: movie,
      headers: ['1', '2', '3', '4'],
      flatObjs: ['a', 'b', 'c', 'd']
    }
  }
}
</script>

<style>

.movie-detail h1 {
  font-size: 20px;
  color: #000;
}

.play-list h2 {
  font-size: 18px;
  color: rgba(0, 0, 0, .85);
  padding-bottom: 10px;
}
</style>
