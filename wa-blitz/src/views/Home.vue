<template>
  <div class="home">
    <table>
      <tr v-for="inf in info" :key="inf.id">
        <td>{{ inf.NAZIV }}</td>
        <td>{{ inf.AUTOR }}</td>
        <td>{{ inf.DATUM }}</td>
      </tr>
    </table>
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
