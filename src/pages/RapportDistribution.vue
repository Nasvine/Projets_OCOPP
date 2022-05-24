
<template>
  <div class="container" style="width: 100%; padding: 0;">
    <!-- Hearder -->
    <div class="header">
      <Header />
    </div>
    <div class="card-panel teal lighten-2" style="margin:0;">
      RAPPORT DES DISTRIBUTIONS
    </div>
    <div class="corps">
      <div class="panel" style="background-color: rgba(227, 222, 222, 1)">
      
        <div class="tab">
              <div class="periode" style="background:none; display:flex; justify-content: flex-end; align-items:flex-end;top:5px; position:relative; bottom:5px;">
                <div id="button" @click="show">
                  <a class="dropdown-trigger btn" href="#" data-target="menu">
                    <span style="position: relative; bottom: 5px">Périodicité</span>
                    <i class="small material-icons">menu</i>
                  </a>
                </div>
              </div>
        </div>
        <div class="row">
          <form v-if="this.set">
            <div id="menu" class="time" style="margin-top: 20px;margin-left: 42%; display: flex; flex-direction: column; ">
              <!-- 1 -->
              <!-- <div class="col s12 m6 l3 box" style="position: relative; display: flex; flex-direction: row; flex-wrap: wrap;">
                <div class="un">
                  <input class="with-gap" style="opacity: 1; pointer-events: auto; left: 0;" name="group1" type="radio" />
                </div>
                <div class="un">
                  <span class="black-text text-darken-2" >Journalier</span>
                </div>
              </div> -->
              <div class="col s12 m6 l3" style="position: relative">
                <div>
                  <input class="with-gap" style="opacity: 1; pointer-events: auto; left: 0; margin-right: 5px; margin-top: 4px;" name="group1"
                    type="radio" />
                </div>
                <div>
                  <span class="black-text text-darken-2" style="margin-left:5px;">Journalier</span>
                </div>
              </div>

              <!-- 2 -->
              <div class="col s12 m6 l3" style="position: relative">
                <div>
                  <input class="with-gap" style="opacity: 1; pointer-events: auto; left: 0; margin-right: 5px; margin-top: 4px;" name="group1"
                    type="radio" />
                </div>
                <div>
                  <span class="black-text text-darken-2" style="margin-left:5px;">Hebdomadaire</span>
                </div>
              </div>
              <!-- 3 -->
              <div class="col s12 m6 l3" style="position: relative">
                <div>
                  <input class="with-gap" style="opacity: 1; pointer-events: auto; left: 0; margin-right: 5px; margin-top: 4px;" name="group1"
                    type="radio" />
                </div>
                <div><span class="black-text text-darken-2" style="margin-left:5px;">Mensuel</span></div>
              </div>
              <!-- 4 -->
              <div class="col s12 m6 l3" style="position: relative">
                <div>
                  <input class="with-gap" style="opacity: 1; pointer-events: auto; left: 0; margin-right: 5px; margin-top: 4px;" name="group1"
                    type="radio" />
                </div>
                <div><span class="black-text text-darken-2" style="margin-left:5px;">Annuel</span></div>
              </div>
            </div>

          </form>

        </div>
        

        <table class="striped" style="padding-left: 20px;">
          <thead>
            <tr>
              <th id="al" style="background-color: rgba(0, 0, 0, 0.53);  color: white; width: 50%; text-align: center;">Produits</th>
              <th id="il" style="background-color: rgba(0, 0, 0, 0.53);  color: white; width: 30%; text-align: center;">Quantité</th>
              <th id="ol" style="background-color: rgba(0, 0, 0, 0.53);  color: white; width: 20%; text-align: center;">Date</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(el, i) in info" class="el" :key="i">

              <td id="al" style="text-align: center;">{{ el.name }}</td>
              <td id="il" style="text-align: center;">{{ el.qty_available }}</td>
              <td id="ol" style="text-align: center;">{{ el.create_date }}</td>
            </tr>
          </tbody>
        </table>





        <!-- <div v-for="(e, index) in table" :key="index">
            {{e}}
            </div> -->
        <!-- <div > {{selection}}</div>  -->

      </div>
    </div>
    <!-- Footer -->
    <div class="Footer">
      <Footer />
    </div>

  </div>


</template>
         
<script>
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';
export default {
  data() {
    return {
      set: false,
      showForm: false,
      product: "",
      quantity: 0,
      info: null,
      loading: true,
      errored: false,




    };
  },
  components: {
    Header, Footer
  },

  methods: {

    show() {
      this.set = !this.set;
      this.showForm = !this.showForm;
    },
  },
  mounted() {
    this.$http
      .get("http://api.odoo.ocoop.rintio.com/odoo/api/v1.0/products/")
      .then((response) => (this.info = response.data))
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
}
</script>


<style scoped lang="scss">
.coprs {
  position: relative;
}

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

.container {

  /* position: absolute; */
  /* top: 50%; */
  /* left: 50%;
  transform: translate(-50%, -50%); */
}

.card-panel {
  position: relative;
  text-align: center;
  color: white;
  font-family: "Times New Roman", Times, serif;
  font-size: 30px;

}

/* .line1{
 font-size: 25px;

} */
.tab {
  margin-left: 40px;
  margin-right: 40px;
}

.button {
  border: none;
  color: white;
  padding: 10px 25px;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 20px 10px;
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 25px;
}

.centre {
  text-align: center;
}

.fill-in {
  fill-opacity: 1;
}

.button1 {
  background-color: teal;
  color: black;
  border: 1px solid rgba(14, 139, 143, 0.522);
}

.button1:hover {
  background-color: rgba(14, 139, 143, 0.522);
  color: white;
}

/* 
.button2 {
  background-color: white;
  color: black;
  border: 1px solid silver;
} */

.button2:hover {
  background-color: silver;
  color: white;
}
.un{
  flex-direction: column;
  padding-left: 10px;
}
</style>
