<template>
  <div>
    <SearchJoke v-on:search-text="searchText" />
    <Joke
      v-for="joke in jokes"
      :key="joke.id"
      :id="joke.id"
      :joke="joke.title"
    />
  </div>
</template>

<script>
import axios from "axios";
import SearchJoke from "../../components/SearchJokes";
import Joke from "../../components/joke";
export default {
  components: {
    Joke,
    SearchJoke,
  },
  data() {
    return {
      jokes: [],
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
        "https://jsonplaceholder.typicode.com/posts",
        config
      );
      this.jokes = res.data;
      console.log(res.data);
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json",
        },
      };
      try {
        const res = await axios.get(
          `https://jsonplaceholder.typicode.com/posts?title=${text}`,
          config
        );
        this.jokes = res.data;
        console.log(res.data);
      } catch (error) {
        console.log(error);
      }
    },
  },
  head() {
    return {
      title: "Welcome jokes",
      meta: [
        {
          hid: "Description",
          name: "description",
          content: "Best Home page design",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
</style>