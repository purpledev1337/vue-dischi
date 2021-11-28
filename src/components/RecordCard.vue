<template>

  <div id="record_card">
    <img :src="recordInfos.poster" alt="">
    <h1>{{ recordInfos.title }}</h1>
    <span id="author_name">{{ recordInfos.author }}</span>
    <span>{{ recordInfos.year }}</span>
  </div>

</template>

<script>
export default {
  name: 'RecordCard',
  props: {
    recordInfos: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#record_card {
  background-color: rgb(46,58,70);
  width: calc(20% - 40px);
  min-width: 150px;
  height: 380px;
  margin: 12px 20px;
  text-align: center;

  img {
    width: 80%;
    padding-top: 20px;
  }

  h1 {
    padding: 15px;
    color: white;
    text-transform: uppercase;
    font-size: 1.5em;
  }

  span {
    width: 80%;
    margin: auto;
    display: block;
    color: rgb(127,127,121);
    font-size: 1.3em;
  }
  
  #author_name {
    margin-top: 10px;
  }
}


</style>
