
<template>
  <div class="container" style="width: 100%">
    <!-- Hearder -->
    <div class="header">
         <Header/>
    </div>
    <div class="ca" style="padding-top:200px;">

    
    <div class="card-panel teal lighten-2" style="margin: 0">
      RAPPORT DES RECEPTIONS
    </div>

    <div id="button" @click="show">
      <a class="dropdown-trigger btn" href="#" data-target="menu">
        <span style="position: relative; bottom: 5px">Périodicité</span>
        <i class="small material-icons">menu</i>
      </a>
    </div>

    <div>
      <div class="row">
        <form v-if="this.set">
          <div id="menu" class="row" style="margin: auto">
            <div class="col s12 m6 l3" style="position: relative">
              <div>
                <input
                  class="with-gap"
                  style="opacity: 1; pointer-events: auto; left: 0; margin: 5px"
                  name="group1"
                  type="radio"
                />
              </div>
              <div>
                <span class="black-text text-darken-2">Journalier</span>
              </div>
            </div>

            <div class="col s12 m6 l3" style="position: relative">
              <div>
                <input
                  class="with-gap"
                  style="opacity: 1; pointer-events: auto; left: 0; margin: 5px"
                  name="group1"
                  type="radio"
                />
              </div>
              <div>
                <span class="black-text text-darken-2">Hebdomadaire</span>
              </div>
            </div>

            <div class="col s12 m6 l3" style="position: relative">
              <div>
                <input
                  class="with-gap"
                  style="opacity: 1; pointer-events: auto; left: 0; margin: 5px"
                  name="group1"
                  type="radio"
                />
              </div>
              <div><span class="black-text text-darken-2">Mensuel</span></div>
            </div>

            <div class="col s12 m6 l3" style="position: relative">
              <div>
                <input
                  class="with-gap"
                  style="opacity: 1; pointer-events: auto; left: 0; margin: 5px"
                  name="group1"
                  type="radio"
                />
              </div>
              <div><span class="black-text text-darken-2">Annuel</span></div>
            </div>
          </div>
        </form>
      </div>
    </div>

    <table class="striped">
      <thead>
        <tr>
          <th id="al">Produits</th>
          <th id="il">Quantité</th>
          <th id="ol">Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(el, i) in info" class="el" :key="i">
          
          <!-- <td id="al">{{ el.name }}</td>
          <td id="il">{{ el.qty_available }}</td>
          <td id="ol">{{ el.create_date }}</td> -->
        </tr>
      </tbody>
    </table>
    <section v-if="errored">
      <p>
        Nous sommes désolés, nous ne sommes pas en mesure de récupérer ces
        informations pour le moment. Veuillez réessayer ultérieurement.
      </p>
    </section>

    <section v-else>
      <div v-if="loading">Chargement...</div>
    </section>
    <div class="Footer">
         <Footer/>
    </div>
    </div>
    
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";

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
    Header,
    Footer,
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

.container {
  position: absolute;
  /* top: 50%; */
  left: 50%;
  
  transform: translate(-50%, -50%);
}

.card-panel {
  position: relative;
  text-align: center;
  color: white;
  font-family: "Times New Roman", Times, serif;
  font-size: 30px;
}

th {
  background-color: rgba(0, 0, 0, 0.53);
  color: white;
}

#button {
  float: right;
  border-radius: 50%;
}

.row {
  float: right;
  align-items: right;
  margin-bottom: auto;
  margin-left: 4px;
}

.row .col {
  float: right;
  box-sizing: content-box;
  padding: 0px 2rem;
  min-height: 17px;
}

.ruban {
  text-align: center;
  font-size: "Times New Roman", Times, serif;
  font-size: 20px;
  background-color: silver;
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 10px;
}
</style>
