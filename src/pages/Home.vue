<template>
  <div class="wrapper-content wrapper-content--fixed">

    <section>
      <div class="container">
        <Search
            :value="search"
            placeholder="Type username..."
        >
        </Search>
      </div>

    </section>

  </div>
</template>

<script>

import Search from "@/components/Search";

export default {
  name: "Home",
  components: {Search},
  data () {
    return {
      search: ''
    }
  }
}
</script>

<style scoped>

</style>