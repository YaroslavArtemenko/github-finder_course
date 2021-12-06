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
<!--        buttons-->
        <button class="btn btnPrimary" @click="getRepos">Search!</button>

<!--        wrapper-->
        <div class="repos__wrapper" v-if="repos">
<!--          item-->
          <div class="repo-item" v-for="repo in repos" :key="repo.id">
            <div class="repo-info">
              <a target="_blank" :href="repo.html_url">{{ repo.name }}</a>
              <span>{{ repo.stargazers_count }} ⭐</span>
            </div>
          </div>
        </div>

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
      search: '',
      repos: null
    }
  },

  methods: {
    getRepos() {
      axios
          .get(`https://api.github.com/users/${this.search}/repos`)
          .then(res => {
            console.log(res)
            this.repos = res.data
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