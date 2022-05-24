
<template>
  <div class="container" style="width: 100%;">
    <div class="card-panel teal lighten-2" style="margin:0;">
      RECEPTION DE PRODUITS
    </div>

    <div class="panel" style="background-color: rgba(227, 222, 222, 1)">
      <div class="tab">
        <div class="row">
          <form class="col s12">
            <div class="row">
              <div class="file-field input-field col s4">
                <div class="btn">
                  <span>Prestataire</span>
                </div>

                <div class="file-path-wrapper" style="padding-left: 0">
                  <input
                    class="file-path validate"
                    style="background-color: white"
                    type="text"
                    placeholder="Nom prestataire"
                  />
                </div>
              </div>

              <div class="file-field input-field col s4">
                <div class="btn">
                  <span>Doc</span>
                  <input type="file" multiple />
                </div>

                <div class="file-path-wrapper" style="padding-left: 0">
                  <input
                    class="file-path validate"
                    style="background-color: white"
                    type="text"
                    placeholder="Document justificatif"
                  />
                </div>
              </div>

              <div class="input-field col s4">
                <input
                  id="icon_date_range"
                  style="background-color: white; color: silver"
                  type="date"
                  class="validate"
                />
              </div>
            </div>
          </form>
        </div>

        <div class="tb">
          <div class="row">
            <form action="col s12">
              <div class="tab2 col s11">
                <table class="striped"  style="width:100%">
                  <thead>
                    <tr > 
                      <th style="background-color: rgba(0, 0, 0, 0.53); color: white;  width:5%"></th>
                      <th  style="background-color: rgba(0, 0, 0, 0.53); text-align: center; color: white; width:80%" scope="col" >Produits</th>
                      <th  style="background-color: rgba(0, 0, 0, 0.53); text-align: center; color: white; whidth:15%" scope="col" >Quantité</th>
            
                    </tr>
                  </thead>

                  <tbody style="background-color: white">
                    <tr v-for="(article, index) in articles" :key="index">
                      <td>
                        <input class="filled-in checkbox-pink" style="opacity:1 ;pointer-events: auto;"
                          :id="index" :value="article" v-model="selected" type="checkbox"/></td>
                      <td>{{ article.name }}</td>
                      <td>{{ article.value }}</td>
                    </tr>
                  </tbody>
                  
                  <tfoot> 
                    <tr>
                      <th colspan= "4" style="padding:15px; background-color: white"  >
                        <div v-if="selected.length>0">
                          <a class="waves-effect waves-light btn-small right" style="background-color: rgba(0, 0, 0, 0.53)" @click="removeThis()">                
                           <i class="material-icons right" >delete</i>Supprimer</a>
                        </div>
                      </th>
                   </tr>
                  </tfoot>

                </table>
              </div>

              <div class="action-btn col s1">
                <a
                  class="btn-floating btn-small waves-effect waves-light"
                  style="background-color: rgba(0, 0, 0, 0.53)"
                  @click="show"
                >
                  <i class="material-icons">add</i>
                </a>
              </div>
            </form>
          </div>
        </div>

        <div class="row">
          <form class="col s12">
            <div v-if="showForm">
              <div class="input-field col s12 m6">
                
                 <select name="Produit" v-model="product">
                    <option value="" disabled selected>Produits</option>
                    <option value="Produit 1">Produit 1</option>
                    <option value="Produit 2">Produit 2</option>
                    <option value="Produit 3">Produit 3</option>
                  </select>
              </div>

              <div class="input-field col s12 m6">
                <input type="number" placeholder="Quantité" v-model="quantity" style="border: 1px solid white; background-color: white;" />
              </div>
            </div>
          </form>
        </div>
      </div>

      <div class="centre">
        <button @click="reset" class="button button1" style="background-color: silver; color: rgba(98, 109, 210, 1); border: 1px solid rgba(98, 109, 210, 1);">Annuler</button>
        <button @click="save"  class="button button2" style="background-color: rgba(98, 109, 210, 1); color: white; border: 1px solid silver;"> Enregistrer</button>
      </div>

      <div v-if="viewForm" style="background-color: teal; color: white; text-align:center;">
        <span style="font-size: x-large;">Reception effectuée avec succès !!!</span>
      </div>
    </div>
  </div>
</template>
         
<script>
export default {
  data() {
    return {
      selected: [],
      showForm: false,
      viewForm: false,
      product: "",
      quantity: "",
      articles: [
        {
          id: 1,
          name: "Produit1",
          value: 10,
        },
        {
          id: 2,
          name: "Produit2",
          value: 20,
        },
        {
          id: 3,
          name: "Produit3",
          value: 30,
        },
      ],
    };
  },

  methods: {
    addThis() {
      
    },
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
          index = this.articles.indexOf(this.selected[i]);
      
          this.articles.splice(index, 1);
        }
      }
      this.selected=[]
    },

    save() {
      if(this.quantity !==0){
        this.articles.push({
        name: this.product,
        value: this.quantity,
      });
      this.quantity= 0 
      this.showForm =false;
      this.viewForm = true;
      setTimeout(()=> {
        this.viewForm = false;
      }, 5000)

      }
    
      
    }
  }
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
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.card-panel {
  text-align: center;
  color: white;
  font-family: "Times New Roman", Times, serif;
  font-size: 35px;

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
