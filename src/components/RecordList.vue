<template>

  <div id="record_list_container">

    <div id="record_card_container"
      v-if="recordList.length === recordListLength"
      >
      <!-- print cards from already filtered list -->
        <RecordCard
        v-for="record, i in filteredRecordList"
        :key="i"
        :recordInfos="record"
        />

    </div>

    <div id="loading_screen" v-else></div>

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
  props: {
    filter: String
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      recordList: [],
      recordListLength : null,
      recordGenreList: []
    }
  },
  created () {
    // demo intent timeout
    setTimeout(() => this.getRecords(), 1000);
  },
  computed: {
    // computed variable to maintain original array data
    filteredRecordList() {
      if (this.filter === "all") {
        return this.recordList
      }
      return this.recordList.filter((element) => {
        return element.genre.includes(this.filter)
      })

    }
  },
  methods: {
    getRecords() {
      axios
      .get(this.apiUrl)
      .then((foundList) => {
        this.recordList = foundList.data.response;
        this.recordListLength = foundList.data.response.length;
        // for loop to generate genre list automatically after api call
        for (let i = 0; i < foundList.data.response.length; i++ ){
          if (!this.recordGenreList.includes(foundList.data.response[i].genre)) {
            this.recordGenreList.push(foundList.data.response[i].genre)
          }
        }
      })
    },
  },
  mounted() {
  this.$emit('genreListCreated', this.recordGenreList)
},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#record_list_container {
  width: 65%;
  min-width: 400px;
  height: calc(100% - 70px);
  min-height: calc(100vh - 70px);
  margin: auto;

  nav {
    height: 80px;
    text-align: center;
    line-height: 80px;
  }

  #record_card_container {
    display: flex;
    flex-wrap: wrap;
    padding-bottom: 50px;
    padding-top: 20px;
  }

  #loading_screen {
    width: 300px;
    height: 300px;
    margin: 20% auto;
    border-radius: 50%;
    border-top: 50px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 50px solid transparent;
    border-left: 50px solid rgb(46,58,70);
    animation: spin 350ms linear infinite;
  }

  @keyframes spin {
    100% { transform: rotate(360deg); }
  }
}
</style>
