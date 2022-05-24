<template>
    <div class="container" style="width:100%;">
         <!-- Hearder -->
        <div class="header">
            <Header/>
        </div>
        <div class="card-panel teal lighten-2" style="margin:0;">
     CONTACTEZ-NOUS
    </div>
    
    <div class="row">
        <form action="" class="col s12">
            <div class="col s5"> 
                <div>
                     <label for="name"> Nom</label>
                     <input type="text" name="" id="name">
                </div>

                 <div>
                     <label for="firstname"> Prénoms</label>
                     <input type="text" name="" id="name">
                </div>

                 <div>
                     <label for="email"> Email</label>
                     <input type="email" name="" id="mail">
                </div>
              

            </div>

            <div class="col s5" style="float: right;"> 
                <div>
                     <label for="objet"> Objet</label>
                     <input type="text" name="" id="objet">

                </div>

                <div>
                    <p>
                        <label for="comments">Message :</label>
	                    <textarea id="comments" rows="5" cols="25" ></textarea>
                    </p>
                </div>
            </div>   
        </form>
    </div>

      <div class="centre">
                <button @click="reset" class="button button1" style="background-color: silver; color: rgba(98, 109, 210, 1); border: 1px solid rgba(98, 109, 210, 1);">Annuler</button>
        
                <button @click="save"  class="button button2" style="background-color: rgba(98, 109, 210, 1); color: white; border: 1px solid silver;"> Envoyer</button>
     </div>
     <!-- Footer -->
    <div class="Footer">
         <Footer/>
    </div>
    </div>
</template>

<script>
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';
export default {
    setup() {
        
    },
    components:{
      Header,Footer
  }
}
</script>

<style>
label{
    font-size: 1.0rem;
    color: #000;
}

textarea{
    height: 7rem;
}

.row{
    margin-top: 25px;
}
.card-panel {
  text-align: center;
  color: white;
  font-family: "Times New Roman", Times, serif;
  font-size: 30px;

}



</style>