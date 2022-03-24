<template>
  <div id="app">
    <div id="nav"></div>
    <router-view />
  </div>
</template>

<script>
export default {
  methods: {
    getData() {
      axios
        .get("https://api.github.com/repos/vuejs/vue/commits")
        .then((response) => {
          response.data.forEach((commits) => {
            this.info.push({
              SHA: commits.sha,
              IME: commits.commit.author.name,
              EMAIL: commits.commit.author.email,
              PORUKA: commits.commit.message,
              DATUM: commits.commit.committer.date,
            });
          });
        });
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

<style lang="scss"></style>
