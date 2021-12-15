<template>
  <v-card>
    <v-card-title>
      Employees
      <v-spacer></v-spacer>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="data"
      :search="search"
      v-if="data"
    ></v-data-table>
  </v-card>
</template>

<script>
const url = "/data.json";
export default {
  data() {
    return {
      data: null,
      search: "",
      headers: [
        { text: "Employee ID",value: "id",},
        { text: "First Name", value: "first_name" },
        { text: "Last Name", value: "last_name" },
        { text: "Gender", value: "gender" },
        { text: "Email", value: "email" },
        { text: "Salary", value: "salary" },
      ],
    };
  },
  async mounted() {
    try {
      const res = await this.$axios.get(url);
      //console.log(res.data);
      this.data = res.data;
    } catch (e) {
      console.error(e);
    }
  },
};
</script>