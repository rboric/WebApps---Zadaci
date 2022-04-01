<template>
  <div class="about">
    <router-link to="/">Go back</router-link>
    <ul>
      <li><b>Name</b></li>
      <li>{{ Information.naziv }}</li>
      <li><b>Autor</b></li>
      <li>{{ Information.autor }}</li>
      <li><b>ISBN</b></li>
      <li>{{ Information.isbn }}</li>
      <li><b>Page Number</b></li>
      <li>{{ Information.brojstranica }}</li>
      <li><b>Publisher</b></li>
      <li>{{ Information.izdavac }}</li>
      <li><b>Country</b></li>
      <li>{{ Information.zemlja }}</li>
      <li><b>Number of characters </b></li>
      <li>{{ Information.brojlikova }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ["info"],
  data() {
    return {
      Information: {},
    };
  },
  mounted() {
    this.url = this.$route.params.url;
    this.Information = this.info.find(
      (Information) => Information.url == this.url
    );
  },
};
</script>
<style scoped>
.about {
  text-align: center;
  width: 50%;
  margin: auto;
}

ul,
a {
  font-family: "Roboto", sans-serif;
}

a {
}

ul {
  list-style-type: none;
}
</style>
