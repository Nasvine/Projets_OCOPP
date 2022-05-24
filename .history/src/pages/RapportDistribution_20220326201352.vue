
<template>
    <div class="container" style="width: 100%;">
        <div class="card-panel teal lighten-2" style="">
            RAPPORT DES DISTRIBUTIONS</div>

        <div id="button" @click="show">
             
            <a class="dropdown-trigger btn" href="#" data-target="menu">
                <span style="position: relative; bottom: 5px;">Périodicité</span> 
                <i class="small material-icons">menu</i>
            </a>
        </div>

         <div>
        <div class="row" >
            <form v-if="this.set">
                <div id="menu" class="row" style="margin: auto;"> 

                    <div class="col s12 m6 l3" style="position: relative;">     
                        <div> <input class="with-gap" style="opacity:1; pointer-events: auto; left: 0; margin: 5px;" name="group1" type="radio"/> </div>                
                        <div> <span class="black-text text-darken-2" >Journalier</span> </div>                     
                    </div>

                    <div class="col s12 m6 l3" style="position: relative;">  
                        <div> <input class="with-gap" style="opacity:1; pointer-events: auto; left: 0; margin: 5px;" name="group1" type="radio"/></div>
                        <div>  <span class="black-text text-darken-2">Hebdomadaire</span></div>                                   
                    </div>

                    <div class="col s12 m6 l3" style="position: relative;">
                        <div> <input class="with-gap" style="opacity:1; pointer-events: auto; left: 0;  margin: 5px;" name="group1" type="radio"/></div>
                        <div>  <span class="black-text text-darken-2">Mensuel</span></div>                   
                    </div>

                    <div class="col s12 m6 l3" style="position: relative;"> 
                        <div> <input class="with-gap" style="opacity:1; pointer-events: auto; left: 0;  margin: 5px;" name="group1" type="radio"/></div>
                        <div>  <span class="black-text text-darken-2">Annuel</span></div>                       
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
                <tr v-for="(article, index) in articles" :key="index">
                    <td id="al" >{{ article.name }}</td>
                    <td id="il">{{ article.value }}</td>
                    <td id="ol">{{ article.date }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>


export default {

    data() {
        return {
            set: false,
            showForm: false,
            product: "",
            quantity: 0,
            articles: [
                {
                    name: "Produit1",
                    value: 10,
                    date: "11/02/2020"
                },
                {
                    name: "Produit2",
                    value: 20,
                    date: "11/02/2020"
                },
                {
                    name: "Produit3",
                    value: 30,
                    date: "11/02/2020"
                },
            ]
        }
    },
    methods: {
        show() {
            this.set = !this.set
            this.showForm = !this.showForm;
        },

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
  height: 90px;
 
}
th{
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
