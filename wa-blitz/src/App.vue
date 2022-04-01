<template>
  <div id="app">
    <router-view v-if="info" :info="info" />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      info: [],
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      axios
        .get("https://www.anapioficeandfire.com/api/books")
        .then((response) => {
          response.data.forEach((books) => {
            this.info.push({
              url: books.url,
              naziv: books.name,
              autor: books.authors,
              datum: books.released,
              isbn: books.isbn,
              brojstranica: books.numberOfPages,
              izdavac: books.publisher,
              zemlja: books.country,
              brojlikova: books.characters.length,
            });
            console.log(this.info);
          });
        });
    },
  },
};
</script>

<style lang="scss"></style>
