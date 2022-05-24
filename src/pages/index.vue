
<template>
  <div class="container" style="width: 100%">
    <!-- Hearder -->
    <div class="header">
      <Header />
    </div>
    <div class="row">
      <div class="col s12 m12">
        <img src="../Rectangle_48.png" />
      </div>
      <!-- <div class=" col s12 m12">
        <div class="card-image col s12 m12">
          
          <div class="text">
            <h1>Card Title</h1>
          </div>
   </div>     
  </div>  -->
    </div>

    <!-- Footer -->
    <div class="Footer">
      <Footer />
    </div>
  </div>
</template>
         
<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";
export default {
  name:'index',
  data() {
    return {};
  },
  components: {
    Header,
    Footer,
  },

  methods: {},
};
</script>


<style>
html,
body {
  height: 100%;
}

body {
  margin: 0;
  background: white;
  font-family: Arial;
  font-weight: 100;
}
.card-image {
  /* display: inline-block;
    position: relative; */
}

.card-image .text {
  /*  background: rgba(0, 0, 0, 0.8);
    z-index: 1;
    position: absolute;
    text-align: center;
    font-family: Georgia;
    margin: 0 auto;
    left: 0;
    right: 0;
    top: 30%;
    color: white;
    width: 70%; */
}
.image {
}

.card {
  background-image: url("../Rectangle_48.png");
  height: 100%;
  width: 100%;
}
.row .col1 {
  float: left;
  box-sizing: border-box;
}
