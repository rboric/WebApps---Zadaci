<template>
  <div class="home">
    <v-text-field
      id="reqData"
      name="name"
      label="Ime"
      counter="15"
      color="purple "
      v-model="inputName"
    ></v-text-field>
    <v-btn @click="getData()" id="reqbutton">Get name information</v-btn>
    <v-data-table :headers="headers" :items="info"></v-data-table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      inputName: "",
      info: [],
    };
  },
  methods: {
    getData() {
      var reqData = this.inputName;
      let one = "https://api.nationalize.io/?name=" + reqData;
      let two = "https://api.agify.io/?name=" + reqData;
      let three = "https://api.genderize.io/?name=" + reqData;

      const requestOne = axios.get(one);
      const requestTwo = axios.get(two);
      const requestThree = axios.get(three);

      axios
        .all([requestOne, requestTwo, requestThree])
        .then((response) => {
          this.info.push({
            name: response[0].data.name,
            country_one: response[0].data.country[0].country_id,
            country_two: response[0].data.country[1].country_id,
            country_three: response[0].data.country[2].country_id,
            countryOneProbability: response[0].data.country[0].probability,
            countryTwoProbability: response[0].data.country[1].probability,
            countryThreeProbability: response[0].data.country[2].probability,
            age: response[1].data.age,
            gender: response[2].data.gender,
            genderProbability: response[2].data.probability,
          });
        })
        .catch((errors) => {
          alert("Name does not exist or contains strange letters.");
        });
    },
  },
  components: {},
  computed: {
    headers() {
      return [
        {
          text: "Name",
          align: "start",

          value: "name",
        },
        {
          text: "Age",
          value: "age",
        },
        { text: "Country 1", value: "country_one" },
        { text: "Country 1 Probability", value: "countryOneProbability" },
        { text: "Country 2", value: "country_two" },
        { text: "Country 2 Probability", value: "countryTwoProbability" },
        { text: "Country 3", value: "country_three" },
        { text: "Country 3 Probability", value: "countryThreeProbability" },
        { text: "Gender", value: "gender" },
        { text: "Gender Probability", value: "genderProbability" },
      ];
    },
  },
};
</script>
<style scoped>
#reqbutton {
  margin-left: 20px;
  background-color: purple;
  color: white;
}

#reqdata {
  margin-left: 5px;
}
</style>
