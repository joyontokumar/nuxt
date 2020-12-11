<template>
  <div>
    <nuxt-link to="/jokes"> </nuxt-link>
    <small>{{ $route.params.id }}</small>
    <hr />
    <h2>{{ joke.title }}</h2>
    <p>{{ joke.body }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: {},
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };
    try {
      const res = await axios.get(
        `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`,
        config
      );
      console.log(res);
      this.joke = res.data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>

<style lang="scss" scoped>
</style>