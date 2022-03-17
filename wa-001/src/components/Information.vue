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
  list-style-type: none;
}
</style>
