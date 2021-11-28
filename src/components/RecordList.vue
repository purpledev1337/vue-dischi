<template>
<div id="record_list_container">
    <RecordCard
    v-for="record, i in recordList"
    :key="i"
    :recordInfos="record"
    />
</div>


</template>

<script>
import axios from "axios";
import RecordCard from './RecordCard.vue'

export default {
  name: 'RecordList',
  components: {
    RecordCard
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
#record_list_container {
  width: 65%;
  min-width: 400px;
  margin: auto;
  display: flex;
  flex-wrap: wrap;
  padding: 60px 0;
}
</style>
