<template>

  <div>
    <img :src="recordInfos.poster" alt="">
    <h1>{{ recordInfos.author }}</h1>
    <span>{{ recordInfos.title }}</span>
    <span>{{ recordInfos.year }}</span>
  </div>

</template>

<script>
export default {
  name: 'RecordInfo',
  props: {
    recordInfos: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">



</style>
