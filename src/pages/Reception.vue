
<template>
  <div class="container" style="width: 100%; padding: 0">
    <!-- Hearder -->
    <div class="header">
      <Header />
    </div>
    <div class="card-panel teal lighten-2" style="margin: 0">
      RECEPTION DES PRODUITS
    </div>

    <div class="corps">
      <div class="panel" style="background-color: rgba(227, 222, 222, 1)">
        <div class="tab">
          <div class="row">
            <form class="col s12">
              <div class="row">
                <div class="file-field input-field col s6">
                  <div class="btn">
                    <span>Prestataire</span>
                  </div>

                  <!-- <input
                    
                      class="file-path-wrapper"
                    class="file-path validate"
                    style="background-color: white"
                    type="text"
                    
                   placeholder="Noms des prestataires"
                    > -->
                  <!-- Partie Search -->
                  <div class="Search">
                    <section class="dropdown-wrapper" style="font-family: Arial">
                      <div @click="isVisible = !isVisible" class="selected-item">
                        <span v-if="selectedItem">{{ selectedItem.name }}</span>
                        <span v-else> Nom du Prestataire</span>
                        <svg class="drop-down-icon" :class="isVisible ? 'dropdown' : 'drop-down-icon'"
                          xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24">
                          <path fill="none" d="M0 0h24v24H0z" />
                          <path d="M12 10.828l-4.95 4.95-1.414-1.414L12 8l6.364 6.364-1.414 1.414z" />
                        </svg>
                      </div>
                      <div :class="isVisible ? 'visible' : 'invisible'" class="dropdown-popover">
                        <input type="text" v-model="searchQuery" placeholder="Search" />
                        <span v-if="filteredUser.length === 0">
                          No Data Available
                        </span>
                        <div class="options">
                          <ul>
                            <li @click="selectItem(partners)" v-for="(partners, index) in filteredUser" class="element"
                              :key="index">
                              {{ partners.name }}
                            </li>
                          </ul>
                        </div>
                      </div>
                    </section>

                    <!-- <section v-if="errored">
                          <p>Nous sommes désolés, nous ne sommes pas en mesure de récupérer ces informations pour le moment. Veuillez réessayer ultérieurement.</p>
                      </section> -->

                    <!-- <section v-else>
                        <div v-if="loading">Chargement...</div>
                      </section> -->
                  </div>
                </div>

                <div class="file-field input-field col s3">
                  <div class="btn">
                    <span>Doc</span>
                    <input type="file" multiple />
                  </div>

                  <div class="file-path-wrapper" style="padding-left: 0">
                    <input class="file-path validate" style="background-color: white" type="text"
                      placeholder="Document justificatif" v-model="document" />
                  </div>
                </div>

                <div class="input-field col s3">
                  <input v-model="date" id="icon_date_range" style="background-color: white; color: silver" type="date"
                    class="validate" />
                </div>
              </div>
            </form>
          </div>

          <div class="tb">
            <div class="row">
              <form action="col s12">
                <div class="tab2 col s11">
                  <table class="striped" style="width: 100%">
                    <thead>
                      <tr>
                        <th style="
                            background-color: rgba(0, 0, 0, 0.53);
                            color: white;
                            width: 5%;
                          "></th>
                        <th style="
                            background-color: rgba(0, 0, 0, 0.53);
                            color: white;
                            width: 50%;
                          " scope="col">
                          Produits
                        </th>
                        <th style="
                            background-color: rgba(0, 0, 0, 0.53);
                            color: white;
                            width: 50%;
                          " scope="col">
                          Quantité
                        </th>
                      </tr>
                    </thead>

                    <tbody style="background-color: white">
                      <tr v-for="(t, index) in tableau" :key="index">
                        <td>
                          <input class="filled-in checkbox-pink" style="opacity: 1; pointer-events: auto" :id="index"
                            v-model="selected" :value="t" type="checkbox" />
                        </td>
                        <td>{{ t.name }}</td>
                        <td>{{ t.quantity_done }}</td>
                      </tr>
                    </tbody>

                    <tfoot>
                      <tr>
                        <th colspan="4" style="padding: 15px; background-color: white">
                          <div v-if="selected.length > 0">
                            <a class="waves-effect waves-light btn-small right"
                              style="background-color: rgba(0, 0, 0, 0.53)" @click="removeThis()">
                              <i class="material-icons right">delete</i>Supprimer</a>
                          </div>
                        </th>
                      </tr>
                    </tfoot>
                  </table>
                </div>

                <div class="action-btn col s1">
                  <a class="btn-floating btn-small waves-effect waves-light"
                    style="background-color: rgba(0, 0, 0, 0.53)" @click="show">
                    <i class="material-icons">add</i>
                  </a>
                </div>
              </form>
            </div>
          </div>
          <!-- Partie pour ajouter les produits -->
          <div class="row">
            <form class="col s12">
              <div v-if="showForm">
                <div class="input-field col s12 m5">
                  <div class="Search_un">
                    <section class="dropdown-wrapper-un">
                      <div @click="isVisible_un = !isVisible_un" class="selected-item-un">
                        <span v-if="selectedItem_un">{{
                            selectedItem_un.name
                        }}</span>
                        <span v-else> Produits</span>

                        <svg class="drop-down-icon-un" :class="isVisible_un ? 'dropdown' : 'drop-down-icon'"
                          xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24">
                          <path fill="none" d="M0 0h24v24H0z" />
                          <path d="M12 10.828l-4.95 4.95-1.414-1.414L12 8l6.364 6.364-1.414 1.414z" />
                        </svg>
                      </div>
                      <div :class="isVisible_un ? 'visible' : 'invisible'" class="dropdown-popover-un">
                        <input type="text" v-model="searchQuery_un" placeholder="Search" />
                        <span v-if="filteredUser_un.length === 0">
                          No Data Available
                        </span>
                        <div class="options">
                          <ul>
                            <li @click="selectItem_un(product)" v-for="(product, index) in filteredUser_un"
                              class="element" :key="index">
                              {{ product.name }}
                            </li>
                          </ul>
                        </div>
                      </div>
                    </section>
                    <!-- <section v-if="errored">
    <p>Nous sommes désolés, nous ne sommes pas en mesure de récupérer ces informations pour le moment. Veuillez réessayer ultérieurement.</p>
  </section>

  <section v-else>
    <div v-if="loading">Chargement...</div>
  </section> -->
                    <!-- <div v-for="(el, index) in tab" :key="index">{{el}}</div> -->
                  </div>
                </div>

                <div class="input-field col s12 m6">
                  <input type="number" placeholder="Quantité" v-model="quantity_ajouter"
                    style="border: 1px solid white; background-color: white" />
                </div>
                <div class="input-field col s12 m1">
                  <button @click="Ajouter" class="waves-effect waves-light btn-small right"
                    style="background-color: rgba(0, 0, 0, 0.53)">
                    OK
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>

        <div class="centre">
          <button @click="reset" class="button button1" style="
              background-color: silver;
              color: rgba(98, 109, 210, 1);
              border: 1px solid rgba(98, 109, 210, 1);
            ">
            Annuler
          </button>
          <button @click="Envoyer" class="button button2" style="
              background-color: rgba(98, 109, 210, 1);
              color: white;
              border: 1px solid silver;
            ">
            Enregistrer
          </button>
        </div>

        <div v-if="viewForm" style="background-color: teal; color: white; text-align: center">
          <span style="font-size: x-large">Reception effectuée avec succès !!!</span>
        </div>
      </div>
    </div>

    <div v-for="(e, index) in table" :key="index">
      {{ e }}
    </div>
    <!-- <div > {{selection}}</div>  -->
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
  data() {
    return {
      searchQuery_un: "",
      selectedItem_un: null,
      isVisible_un: false,
      products: null,
      selection: "",

      selection_id: null,
      showForm: false,
      viewForm: false,
      info: null,
      loading: true,
      errored: false,
      searchQuery: "",
      selectedItem: null,
      isVisible: false,
      partners: "",
      tableau: [],
      quantity_ajouter: null,
      produit_entrer: "",
      selected: [],
      tab: [],
      partner_id: "",
      name_of_partner: "",
      id_produits: null,
      date: null,
      document: "",
      table: [],
      product_id: "",
      
    };
  },
  components: {
    Header,
    Footer,
  },

  methods: {

    getItem() {
      let Utilisateur = localStorage.getItem("users");
      /* console.log("la compagny est :", Utilisateur);*//* 
      console.log("le type est :", typeof ( parseInt(Utilisateur)));  */
      return parseInt(Utilisateur);

    },

    selectItem_un(product) {
      this.selectedItem_un = product;
      this.tab.push({ id: product.id });
      this.selection = product.name;
      this.product_id = product.id;
      this.isVisible_un = false;
    },
    Ajouter() {
      if (this.quantity_ajouter !== 0) {
        this.tableau.push({
          product_id: this.product_id,
          name: this.selection,
          quantity_done: parseInt(this.quantity_ajouter),
        });
        this.quantity_ajouter = 0;
        this.showForm = false;
        setTimeout(() => {
          this.viewForm = false;
        }, 5000);
      }
    },

    Envoyer() {
      /* console.log("le type est :", typeof (company_id)); */
      /* console.log(company_id); */
      this.$http
        .post(
          "http://api.odoo.ocoop.rintio.com/odoo/api/v1.0/receipts/",

          this.table.push({

            partner_id: this.partner_id,
            company_id: parseInt(this.getItem()),
            /* date: this.date, */
            move_lines: this.tableau,
            
          })
          
        )
        .catch((error) => {
          console.log(error);
          this.errored = true;
        });
      console.log(this.table);

    }
    ,
    selectItem(partners) {
      this.selectedItem = partners;
      this.partner_id = partners.id;
      /* this.name_of_partner = partners.name; */
      this.isVisible = false;
    },

    /* Supprimer(index){
      this.tableau.splice(index, 1)

    }, */
    addThis() { },
    show() {
      this.showForm = !this.showForm;
    },
    reset() {
      this.showForm = false;
    },

    removeThis: function () {
      let index = 0;
      if (confirm("Voulez-vous supprimer définitivement?")) {
        for (let i = 0; i < this.selected.length; i++) {
          index = this.tableau.indexOf(this.selected[i]);

          this.tableau.splice(index, 1);
        }
      }
      this.selected = [];
    },

    save() {
      if (this.qty_available !== 0) {
        this.info.push({
          name: this.name,
          value: this.qty_available,
        });
        this.qty_available = 0;
        this.showForm = false;
        this.viewForm = true;
        setTimeout(() => {
          this.viewForm = false;
        }, 5000);
      }
    },
  },
  mounted() {


    this.$http
      .get("http://api.odoo.ocoop.rintio.com/odoo/api/v1.0/products/")
      .then((response) => (this.products = response.data))
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));

    this.$http
      .get("http://api.odoo.ocoop.rintio.com/odoo/api/v1.0/partners/")
      .then((response) => (this.partners = response.data))
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
  computed: {
    filteredUser() {
      const query = this.searchQuery.toLowerCase();
      if (this.searchQuery === "") {
        return this.partners;
      }
      return this.partners.filter((partners) => {
        return Object.values(partners).some((word) =>
          String(word).toLowerCase().includes(query)
        );
      });
    },
    filteredUser_un() {
      const query = this.searchQuery_un.toLowerCase();
      if (this.searchQuery_un === "") {
        return this.products;
      }
      return this.products.filter((product) => {
        return Object.values(product).some((word) =>
          String(word).toLowerCase().includes(query)
        );
      });
    },
  },
};
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

/* CSS de search */

.dropdown-wrapper {
  max-width: 314px;
  position: relative;
  margin: 0 auto;
  background-color: #fff;
}

.selected-item {
  height: 46px;
  /*border: 2px solid lightgray;
     border-radius: 5px; */
  padding: 5px 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 18px;
  font-weight: 400;

  .drop-down-icon {
    transform: rotate(0deg);
    transition: all 0.4s ease;

    &.dropdown {
      transform: rotate(180deg);
    }
  }
}

.dropdown-popover {
  position: absolute;
  border: 2px solid rgb(255, 255, 255);
  top: 46px;
  left: 0;
  right: 0;
  background-color: #fff;
  max-width: 100%;
  padding: 0px;
  visibility: hidden;
  transition: all 0.5s linear;
  max-height: 0px;
  overflow: hidden;

  &.visible {
    max-height: 450px;
    visibility: visible;
  }

  input {
    width: 90%;
    height: 30px;
    border: 2px solid lightgray;
    font-size: 16px;
    padding-left: 5px;
  }

  .options {
    width: 100%;

    ul {
      list-style: none;
      text-align: left;
      padding-left: 8px;
      max-height: 180px;
      overflow-y: scroll;
      overflow-x: hidden;
      border: 1px solid lightgray;

      li {
        width: 100%;
        border-bottom: 1px solid lightgray;
        padding: 10px;
        background-color: #fafafa;
        cursor: pointer;
        font-size: 16px;

        &:hover {
          background: #70878a;
          color: #fff;
          font-weight: bold;
        }
      }
    }
  }
}

/* CSS Search_un */

.dropdown-wrapper-un {
  max-width: 600px;
  position: relative;
  margin: 0 auto;
  background-color: #fff;
  height: 48px;
}

.selected-item-un {
  height: 40px;
  border: 2px solid #fff;
  padding: 5px 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 18px;
  font-weight: 400;

  .drop-down-icon-un {
    transform: rotate(0deg);
    transition: all 0.4s ease;

    &.dropdown {
      transform: rotate(180deg);
    }
  }
}

.dropdown-popover-un {
  position: absolute;
  border: 2px solid #fff;
  top: 46px;
  left: 0;
  right: 0;
  background-color: #fff;
  max-width: 100%;
  padding: 20px;
  visibility: hidden;
  transition: all 0.5s linear;
  max-height: 0px;
  overflow: hidden;

  &.visible {
    max-height: 450px;
    visibility: visible;
  }

  input {
    width: 90%;
    height: 30px;
    border: 2px solid rgb(175, 171, 171);
    font-size: 16px;
    padding-left: 5px;
  }

  .options {
    width: 100%;

    ul {
      list-style: none;
      text-align: left;
      padding-left: 8px;
      max-height: 180px;
      overflow-y: scroll;
      overflow-x: hidden;
      border: 1px solid lightgray;

      li {
        width: 100%;
        border-bottom: 1px solid lightgray;
        padding: 10px;
        background-color: #f1f1f1;
        cursor: pointer;
        font-size: 16px;

        &:hover {
          background: #70878a;
          color: #fff;
          font-weight: bold;
        }
      }
    }
  }
}
</style>
