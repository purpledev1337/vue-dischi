<template>

  <div id="app">

    <header>
      <img src="./assets/logo-small.svg" alt="">
      <FilterMenu
      :recordGenres="recordGenreList"
      @filterGenre="selectFilter"
      />
    </header>

    <main>
      <RecordList
      :filter="genreToFilter"
      @genreListCreated="getList"/>
    </main>

  </div>
  
</template>

<script>

import RecordList from './components/RecordList.vue'
import FilterMenu from './components/FilterMenu.vue'

export default {
  name: 'App',
  components: {
    RecordList,
    FilterMenu
  },
  data() {
    return {
      recordGenreList: [],
      genreToFilter: null
    }
  },
  methods: {
    getList(recordGenreList) {
      this.recordGenreList = recordGenreList
      console.log("lista presa dal figlio",this.recordGenreList);
    },
    selectFilter(genreToFilter) {
      if (genreToFilter === "all") {
        this.genreToFilter = null
      }
      else {
        this.genreToFilter = genreToFilter
        console.log(this.genreToFilter);
      }
    }
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  background-color: rgb(30,45,59);
  min-width: 720px;

  header {
    height: 70px;
    background-color: rgb(46,58,70);
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      height: 40px;
      margin: 15px 20px;
    }
  }
}
</style>
