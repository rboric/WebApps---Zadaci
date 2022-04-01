<template>
  <div class="about">
    <router-link to="/">Go back</router-link>
    <ul>
      <li>{{ Information.naziv }}</li>
      <li>{{ Information.autor }}</li>
      <li>{{ Information.isbn }}</li>
      <li>{{ Information.brojstranica }}</li>
      <li>{{ Information.izdavac }}</li>
      <li>{{ Information.zemlja }}</li>
      <li>Number of characters:{{ Information.BROJLIKOVA }}</li>
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
      (Information) => (Information.url = this.url)
    );
  },
};
</script>
<style scoped>
ul {
  list-style-type: none;
}
</style>
