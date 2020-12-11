<template>
  <form @submit.prevent="onSubmit">
    <label>
      <input type="text" v-model="text" placeholder="Search Jokes" />
      <input type="submit" value="search joke" />
    </label>
  </form>
</template>

<script>
export default {
  name: "SearchJokes",
  data() {
    return {
      text: "",
    };
  },
  methods: {
    onSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    },
  },
};
</script>

<style lang="scss" scoped>
</style>