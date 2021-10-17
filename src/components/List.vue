<template>
  <main id="main">
    <ul class="list-container clearfix">
      <li v-for="user in info.users" :key="user.node_id" v-show="info.users.length">
        <a :href="user.html_url">
          <img :src="user.avatar_url" :alt="user.avatar_url"> <br>
          <span>{{user.login}}</span>
        </a>
      </li>
    </ul>
<!--    welcome-->
    <h1 v-show="info.isFirst">welcome and use this</h1>
<!--    loading-->
    <h1 v-show="info.isLoading">Loading...</h1>
<!--    err msg-->
    <h1 v-show="info.errMsg">meet some error - {{info.errMsg}}</h1>
  </main>
</template>

<script>
export default {
  name: "List",
  data() {
    return {
      info: {
        isFirst: true,
        isLoading: false,
        errMsg: "",
        users: []
      }
    }
  },
  mounted() {
    this.$bus.$on("data", (dataObj)=>{
      this.info = dataObj;
    })
  },
  beforeDestroy() {
    this.$bus.$off("data");
  }
}
</script>

<style scoped>
  #main {
    margin-top: 20px;
  }

  .list-container {
    padding-left: 10px;
  }

  .list-container li {
    float: left;
    text-align: center;
    width: 300px;
    margin-right: 25px;
    margin-bottom: 10px;
    border: 1px solid gray;
  }
  .list-container li:nth-child(4n) {
    margin-right: 0;
  }

  ul li a {
    text-decoration: none;
    color: inherit;
  }

  ul li img {
    width: 50px;
    border-radius: 50%;
  }

  .list-container li:hover {
    cursor: pointer;
    color: #fff;
    background-color: gray;
  }
</style>