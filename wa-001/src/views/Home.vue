<template>
  <div class="home">
    <ul>
      <li v-for="inf in info" :key="inf.id">
        <router-link to="/about">SHA: {{ inf.SHA }}</router-link>
        <information :information="inf" />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import Information from "../components/Information.vue";

export default {
  components: { Information },
  name: "Home",
  data() {
    return {
      info: [],
    };
  },
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
<style scoped>
.home {
  width: 50%;
  height: 100vh;
  margin: auto;
  text-align: center;
}

li {
  list-style-type: none;
  padding: 20px;
}

li a {
  font-size: 20px;
  color: black;
  text-decoration: none;
}

li a:hover {
  color: red;
  transition: 0.1s;
}
</style>
