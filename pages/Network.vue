<template>
  <v-card>
    <v-card-title>
      เครือข่ายพันธมิตรทั้งภาครัฐและเอกชน (Univesities , Organization)
      <v-spacer></v-spacer><v-spacer /><v-spacer /><v-spacer />
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="ค้นหา"
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
const url = "/network.json";
export default {
  data() {
    return {
      data: null,
      search: "",
      headers: [
        { text: "ลำดับที่",value: "network_ID",},
        { text: "ชื่อหน่วยงาน", value: "network_name" },
        { text: "Website /Facebook", value: "network_website" },
        { text: "รายละเอียดการให้บริการ", value: "network_service" },
        { text: "หมายเหตุ", value: "note" },
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