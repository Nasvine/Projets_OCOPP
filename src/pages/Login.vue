<template>

<div class="container">
   <div class="vue-tempalte">
        <div id="img">
            <center> <g-image alt="Example image" src="~/index.jpg" width="200" /> </center>
        </div>
        
        <form>
           
            <div class="mail">
                <label>Email</label>
                <input type="email" class="form-control form-control-lg" />
            </div>
            <div class="mail">
                <label>Mot de passe</label>
                <input type="password" class="form-control form-control-lg" />
            </div>
            <button type="submit" class="btn">Connexion</button>
           <!--  <center>
            <p class="forgot-password text-right mt-2 mb-4"> 
               <a href="login.vue.html" title="Mot de passe oublié?"><span>Mot de passe oublié?</span></a>
               </p>
               </center> -->
               <!--  <p class="mdp">Mot de passe oublié ?</p> -->
                
        </form>
    </div>
     </div> 
</template>


<style>
.btn{
  justify-content: center;
  background-color: rgb(2, 2, 85);
  width: 40%;
  margin-top: 3%;
  margin-left:38%;
}
.mdp{
  color: black;
  text-align: center;
}
.mail{
  width: 75%;
  margin-left: 20%;
  justify-content: center;
}
</style>
