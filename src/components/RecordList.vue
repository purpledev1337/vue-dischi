<template>
<div>
    <RecordInfo
    v-for="record, i in recordList"
    :key="i"
    :recordInfos="record"
    />
</div>


</template>

<script>
import axios from "axios";
import RecordInfo from './RecordInfo.vue'

export default {
  name: 'RecordList',
  components: {
    RecordInfo
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      recordList: []
    }
  },
  created () {
    this.getRecords();
  },
  methods: {
      getRecords() {
        axios
        .get(this.apiUrl)
        .then((foundList) => {
          this.recordList = foundList.data.response
          console.log(foundList.data.response);
        })
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">



</style>
