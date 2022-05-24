<template>
 <div class="container"> 

   <div class="card-panel teal lighten-2">DISTRIBUTION DE PRODUITS</div>

  <div class="row">
    <form class="col s12">

     <div class="row">
       <!--  <div class="input-field col s4">
          <i id="account_circle" class="material-icons prefix">account_circle</i>
          <input id="icon_prefix" type="text" class="validate" placeholder="Nom du Bénéficiaire">
      </div> -->

     
      <div class="file-field input-field col s4">
            <div class="btn">
            <span>Doc</span>
            <input type="file" multiple>
      </div>

      <div class="file-path-wrapper">
        <input class="file-path validate" type="text" placeholder="Document justificatif">
      </div>

        </div>

        <div class="input-field col s4">
          <input id="icon_date_range" type="date" class="validate" >
        </div>
      </div>
    </form>
  </div>

  <div class="row">
    <div class="col s12 m6 l11" >
      <table class="highlight striped ">
        <thead>
          <tr>
           <!--    <th>Produits</th>
              <th id="th_center">Quantité</th>
              <th id="th_center">Supprimer</th> -->
          </tr>
        </thead>
        
        <tbody>
         <!--  <tr v-for="(article,index) in articles" :key="index">
            <td>{{article.name}}</td>
            <td id="th_center">{{article.value}}</td>
            <td id="th_center">
              <i class="material-icons" @click="removeThis(index)">delete</i>
            </td>
          </tr> -->
        </tbody>
      </table>
    </div>
    <div class="col s12 m6 l1">
      <a class="btn-floating btn-large waves-effect waves-light"><i class="material-icons" @click="show">add</i></a>
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
            <input type="number" v-model="quantity" placeholder="Quantité"/> 
        </div>    
      </div>
    </form>
     
 </div>
  
  <div class="centre">
    <button @click="save" class="button button1">Enregistrer</button>
    <button @click="show" class="button button2">Annuler</button>
  </div>
</div>
</template>

<script>
export default {
  metaInfo: {
   /*  title: 'Distribution' */
  },
 /*  methods: {
    currentDateTime() {
      const current = new Date();
      const date = current.getFullYear()+'/'+(current.getMonth()+1)+'/'+current.getDate();
      return date;
    }
  }, */
  data(){
    return{
      showForm:false,
      product:"",
      quantity: '',
      articles : [
      ],
     /*  options:{
        classes : "",
        dropdownOptions : {}
      } */
    }
  },
  methods:{
    show(){
      this.showForm=!this.showForm;
    },
    removeThis(index){
      this.articles.splice(index,1);
    },
    save(){
      this.articles.push(
        {
          name:this.product,
          value:this.quantity
        }
      );
      this.showForm=!this.showForm;
    },
   /*  mounted(){
      var elems = document.querySelectorAll('select');
      this.show();
    } */
  }
}
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
	/* position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%); */
}
.card-panel{
  text-align: center;
  color: white;
  font-family: 'Times New Roman', Times, serif;
  font-size: 28px;
  border-radius: 10px;
} 
.highlight {
	border-collapse: collapse;
	overflow: hidden;
  border-radius: 10px;
	
}
/* #account_circle{
  color: teal;
} */
th {
  font-family: 'Times New Roman',"Segoe UI";
  font-size: 20px;
  height: 10px;
	background-color:silver;
	color:black;	
}
#th_center{
  text-align: center;
}
td {
  font-size: 13px;
	padding: 15px;
	color:black;
}
/* #td_right{
  text-align: right;
} */
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
.centre{
  text-align: center; 
}
.button1 {
  background-color: teal; 
  color: black; 
  border: 1px solid rgba(14, 139, 143, 0.522);
}
.button1:hover {
  background-color:rgba(14, 139, 143, 0.522);
  color: white;
}
.button2 {
  background-color: white; 
  color: black; 
  border: 1px solid silver;
}
.button2:hover {
  background-color:silver;
  color: white;
}
/* select{
  display: inline-block !important;

} */
</style>
