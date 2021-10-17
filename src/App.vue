<template>
  <div id="app">
    <Search></Search>
    <List></List>
  </div>
</template>

<script>
import Search from "./components/Search";
import List from "./components/List";

export default {
  name: 'App',
  components: {
    Search,
    List
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  #app {
    width: 1300px;
    margin: 0 auto;
  }
  ul {
    margin: 0;
    padding: 0;
  }
  ul li{
    list-style: none;
  }

  .clearfix:after{
    content: "";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
  }

  .clearfix {
    *zoom: 1;
  }
</style>
