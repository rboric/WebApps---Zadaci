<template>
  <div>
    <ul>
      <li>IME: {{ information.IME }}</li>
      <li>EMAIL: {{ information.EMAIL }}</li>
      <li>PORUKA: {{ information.PORUKA }}</li>
      <li>DATUM: {{ information.DATUM }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["information"],
  name: "Information",
};
</script>
<style scoped>
li {
  padding: 4px;
  list-style-type: none;
}

ul {
  margin-top: 20px;
}
</style>
