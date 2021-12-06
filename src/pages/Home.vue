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
        <button class="btn btnPrimary">Search!</button>
      </div>

    </section>

  </div>
</template>

<script>

import Search from "@/components/Search";

export default {
  name: "Home",
  components: {Search},
  data() {
    return {
      search: ''
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
</style>