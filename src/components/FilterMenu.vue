<template>

    <!-- send to the parent the selected option value -->
    <select @change="$emit('filter', selected)"
        v-model="selected"
        name="type_list">
            <option
            disabled
            value="">
                Select music genre
            </option>
            <option
            value="all">
                All genres
            </option>
            <!-- printing of all genres found -->
            <option
            v-for="genre, i in recordGenres"
            :key="i"
            :value="i">
                {{ genre }}
            </option>

    </select>

</template>

<script>
export default {
  name: 'FilterMenu',
//   genre list taken from parent
  props: {
      recordGenres: Array
  },
  data() {
      return {
          selected: null
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

select {
    width: 200px;
    transform: scale(1.5);
}

</style>
