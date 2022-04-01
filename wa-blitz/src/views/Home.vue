<template>
  <div class="home">
    <ul v-for="inf in info" :key="inf.id">
      <li>
        <router-link :to="{ name: 'About', params: { url: inf.url } }">
          <b>{{ inf.naziv }}</b></router-link
        >
      </li>
      <li>{{ inf.autor[0] }}</li>
      <li>{{ inf.izdavac }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["info"],
  name: "Home",
  data() {
    return {};
  },
  mounted() {},
  methods: {},
  components: {},
};
</script>
<style scoped>
.home {
  width: 50%;
  margin: auto;
  text-align: center;
}

ul {
  list-style-type: none;
}

a {
  text-decoration: none;
}
</style>
