<template>
  <header id="header">
    <h2>Search Github Users</h2>
    <input type="text" placeholder="enter the name you want to search" v-model="keyword">
    <button @click="searchKeyWord">Search</button>
  </header>
</template>

<script>
import axios from "axios";

export default {
  name: "Search",
  data() {
    return {
      keyword: ""
    }
  },
  methods: {
    searchKeyWord() {
      this.$bus.$emit("data", {isFirst: false, isLoading: true, errMsg: "", users: []})
      axios({
        url: "https://api.github.com/search/users",
        params: {
          q: this.keyword
        },
        method: "GET"
      }).then(value => {
        this.$bus.$emit("data", {isLoading: false, errMsg: "", users: value.data.items});
      }).catch(reason => {
        this.$bus.$emit("data", {isLoading: false, errMsg: reason.message, users: []});
      })
    }
  }
}
</script>

<style scoped>
  #header {
    height: 200px;
    background-color: gray;
    padding: 80px 0 0 50px;
  }

  #header input {
    width: 230px;
    outline: none;
  }

</style>