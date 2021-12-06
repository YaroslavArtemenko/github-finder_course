<template>
  <div class="wrapper-content wrapper-content--fixed">

    <section>
      <div class="container">

        <!--        search-->
        <Search
            :value="search"
            placeholder="Type username..."
            @search="search = $event"
        >
        </Search>
        <button class="btn btnPrimary" @click="getRepos">Search!</button>
      </div>

    </section>

  </div>
</template>

<script>

import Search from "@/components/Search";
import axios from 'axios'

export default {
  name: "Home",
  components: {Search},
  data() {
    return {
      search: ''
    }
  },

  methods: {
    getRepos() {
      axios
          .get(`https://api.github.com/users/${this.search}/repos`)
          .then(res => {
            console.log(res)
          })
          .catch(err => {
            console.log(err)
          })
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  align-items: center;
  flex-direction: column;
}

button {
  margin-top: 40px;
}
</style>