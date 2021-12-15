<template>
  <div>
    <h1>Dashboard</h1>
    <v-row>
      <v-col md="6">
        <v-card>
          <line-chart
            :linechartdata="chartdata"
            :linechartoptions="options"
            :height="300"
          />
        </v-card>
      </v-col>
      <v-col md="6">
        <v-card>
          <bar-chart
            :barchartdata="barchartdata"
            :barchartoptions="barchartoptions"
            :height="300"
          />
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-card v-if="loaded">
          <line-chart
            :linechartdata="jsonchartdata"
            :lineoptions="barchartoptions"
            :height="300"
          />
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
const url = "/data.json";

export default {
  data() {
    return {
      chartdata: {
        labels: ["January", "February", "March", "April"],
        datasets: [
          {
            label: "Data One",
            borderColor: "#f87979",
            data: [40, 20, 50, 10],
            fill: false
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false
      },
      barchartdata: {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [
          {
            label: "# of Votes",
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
              "rgba(75, 192, 192, 0.2)",
              "rgba(153, 102, 255, 0.2)",
              "rgba(255, 159, 64, 0.2)"
            ],
            borderColor: [
              "rgba(255, 99, 132, 1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
              "rgba(75, 192, 192, 1)",
              "rgba(153, 102, 255, 1)",
              "rgba(255, 159, 64, 1)"
            ],
            borderWidth: 1
          }
        ]
      },
      barchartoptions: {
        responsive: true,
        maintainAspectRatio: false,
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true
              }
            }
          ]
        }
      },
      loaded: false,
      apichartdata: {
        labels: [],
        datasets: []
      },
      jsonchartdata: {
        labels: [],
        datasets: []
      },
    };
  },
  async mounted(){
      this.loaded = false;
      try {
        const res = await this.$axios.get(url);
        var results = res.data;
        var tmplabels = [],tmpdata = [];
        results.forEach(function(x) {
          tmplabels.push(x.id);
          tmpdata.push(parseFloat(x.salary));
        });

        var tempData = {
          labels: tmplabels,
          datasets: [
            {
              label: "Salary by ID",
              data: tmpdata,
              borderColor: "rgb(75, 192, 192)",
              backgroundColor: "rgba(75, 192, 192, 0.2)"
            }
          ]
        };
        this.jsonchartdata = tempData;
        this.loaded = true;
      } catch (e) {
        console.error(e);
      }
  }
};
</script>
