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
        .get("http://ntankovic.unipu.hr:8000/books.json")
        .then((response) => {
          response.data.forEach((books) => {
            this.info.push({
              NAZIV: books.name,
              AUTOR: books.authors[0],
              DATUM: books.released,
            });
            console.log(this.info);
          });
        });
    },
  },
};
</script>

<style lang="scss"></style>
