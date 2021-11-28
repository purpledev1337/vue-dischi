<template>
  <div id="app">

    <header>
      <img src="./assets/logo-small.svg" alt="">
    </header>

    <main>
      <RecordList/>
    </main>

  </div>
</template>

<script>

import RecordList from './components/RecordList.vue'

export default {
  name: 'App',
  components: {
    RecordList
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
}

header {
  height: 70px;
  background-color: rgb(46,58,70);

  img {
    height: 40px;
    margin: 15px 20px;
  }
}


</style>
