<template>
  <v-card>
    <v-card-title>
      ผู้เชี่ยวชาญ (Expert)
      <v-spacer></v-spacer><v-spacer /><v-spacer /><v-spacer />
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="ค้นหา"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>
    <nav>
      <div class="nav justify-content-center" id="nav-tab" role="tablist">
        <a
          class="nav-item nav-link active"
          id="nav-home-tab"
          data-toggle="tab"
          href="#nav-ชา"
          role="tab"
          aria-controls="nav-ชา"
          aria-selected="true"
          >ชา</a>
        <a
          class="nav-item nav-link"
          id="nav-profile-tab"
          data-toggle="tab"
          href="#nav-กาแฟ"
          role="tab"
          aria-controls="nav-กาแฟ"
          aria-selected="false"
          >กาแฟ</a>
        <a
          class="nav-item nav-link"
          id="nav-contact-tab"
          data-toggle="tab"
          href="#nav-อาหารอื่นๆ"
          role="tab"
          aria-controls="nav-อาหารอื่นๆ"
          aria-selected="false"
          >อาหารอื่นๆ</a>
      </div>
    </nav>
    <div class="container">
      <div class="row">
        <!-- Team member -->
        <div class="col-xs-12 col-sm-6 col-md-4">
          <div class="image-flip">
            <div class="mainflip flip-0">
              <div class="frontside">
                <div class="card">
                  <div class="card-body text-center">
                    <p>
                      <img class="img-fluid" src="38.jpg" alt="card image" />
                    </p>
                    <h4 class="card-title">ชื่อ-นามสกุล :</h4>
                    <p class="card-text">หน่วยงาน : </p>
                    <a
                      href="https://www.fiverr.com/share/qb8D02"
                      class="btn btn-primary btn-sm"
                      ><i class="fa fa-plus"></i
                    ></a>
                  </div>
                </div>
              </div>
              <div class="backside">
                <div class="card">
                  <div class="card-body text-center mt-4">
                    <h4 class="card-title">ข้อมูลเพิ่มเติม</h4>
                    <p class="card-text">ชื่อ-นามสกุล : </p>
                    <p class="card-text">หน่วยงาน : </p>
                    <h4 class="card-title">ข้อมูลความเชี่ยวชาญ</h4>
                    <p class="card-text">ความเชี่ยวชาญ : </p>
                    <p class="card-text">ผลงานวิจัย : </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- ./Team member -->
      </div>
    </div>
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

<style>
/* FontAwesome for working BootSnippet :> */

@import url("https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css");

/* style card */
#team {
  background: #eee !important;
}

section {
  padding: 60px 0;
}

section .section-title {
  text-align: center;
  color: #007b5e;
  margin-bottom: 50px;
  text-transform: uppercase;
}

#team .card {
  border: none;
  background: #ffffff;
}

.image-flip:hover .backside,
.image-flip.hover .backside {
  -webkit-transform: rotateY(0deg);
  -moz-transform: rotateY(0deg);
  -o-transform: rotateY(0deg);
  -ms-transform: rotateY(0deg);
  transform: rotateY(0deg);
  border-radius: 0.25rem;
}

.image-flip:hover .frontside,
.image-flip.hover .frontside {
  -webkit-transform: rotateY(180deg);
  -moz-transform: rotateY(180deg);
  -o-transform: rotateY(180deg);
  transform: rotateY(180deg);
}

.mainflip {
  -webkit-transition: 1s;
  -webkit-transform-style: preserve-3d;
  -ms-transition: 1s;
  -moz-transition: 1s;
  -moz-transform: perspective(1000px);
  -moz-transform-style: preserve-3d;
  -ms-transform-style: preserve-3d;
  transition: 1s;
  transform-style: preserve-3d;
  position: relative;
}

.frontside {
  position: relative;
  -webkit-transform: rotateY(0deg);
  -ms-transform: rotateY(0deg);
  z-index: 2;
  margin-bottom: 30px;
}

.backside {
  position: absolute;
  top: 0;
  left: 0;
  background: white;
  -webkit-transform: rotateY(-180deg);
  -moz-transform: rotateY(-180deg);
  -o-transform: rotateY(-180deg);
  -ms-transform: rotateY(-180deg);
  transform: rotateY(-180deg);
  -webkit-box-shadow: 5px 7px 9px -4px rgb(158, 158, 158);
  -moz-box-shadow: 5px 7px 9px -4px rgb(158, 158, 158);
  box-shadow: 5px 7px 9px -4px rgb(158, 158, 158);
}

.frontside,
.backside {
  -webkit-backface-visibility: hidden;
  -moz-backface-visibility: hidden;
  -ms-backface-visibility: hidden;
  backface-visibility: hidden;
  -webkit-transition: 1s;
  -webkit-transform-style: preserve-3d;
  -moz-transition: 1s;
  -moz-transform-style: preserve-3d;
  -o-transition: 1s;
  -o-transform-style: preserve-3d;
  -ms-transition: 1s;
  -ms-transform-style: preserve-3d;
  transition: 1s;
  transform-style: preserve-3d;
}

.frontside .card,
.backside .card {
  min-height: 250px;
  min-width: 250px;
}

.backside .card a {
  font-size: 18px;
  color: #007b5e !important;
}

.frontside .card .card-title,
.backside .card .card-title {
  color: #007b5e !important;
}

.frontside .card .card-body img {
  width: 120px;
  height: 120px;
  border-radius: 50%;
}
/* style card */

/* style tab */
.project-tab {
    padding: 10%;
    margin-top: -8%;
}
.project-tab #tabs{
    background: #007b5e;
    color: #eee;
}
.project-tab #tabs h6.section-title{
    color: #eee;
}
.project-tab #tabs .nav-tabs .nav-item.show .nav-link, .nav-tabs .nav-link.active {
    color: #0062cc;
    background-color: transparent;
    border-color: transparent transparent #f3f3f3;
    border-bottom: 3px solid !important;
    font-size: 16px;
    font-weight: bold;
}
.project-tab .nav-link {
    border: 1px solid transparent;
    border-top-left-radius: .25rem;
    border-top-right-radius: .25rem;
    color: #0062cc;
    font-size: 16px;
    font-weight: 600;
}
.project-tab .nav-link:hover {
    border: none;
}
.project-tab thead{
    background: #f3f3f3;
    color: #333;
}
.project-tab a{
    text-decoration: none;
    color: #333;
    font-weight: 600;
}
/* style tab */
</style>