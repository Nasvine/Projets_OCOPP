<template>
  <header>
    <div class="card-panel white lighten-2"> 
        
        <div class="row" style="display: flex; justify-content: flex-end;">
        <div class="col">
           <a class="waves-effect waves-light btn-small">Réception</a>

        </div>

         <div class="col">
            <a class="waves-effect waves-light btn-small">Distribution</a>
        </div>

         <div class="col">
             <a class='dropdown-trigger btn' href='#' data-target='dropdown1' @click= "toggle" >Rapport</a>
                <ul id='dropdown1' class='dropdown-content' v-if="isOpen">
                    <li><a href="#!">Reception</a></li>
                    <li class="divider" tabindex="-1"></li>
                    <li><a href="#!">Distribution</a></li>
                </ul>   
        </div>

         <div class="col">
            <a class="waves-effect waves-light btn-small">Contactez-nous</a> 
        </div>
        
    </div>

    </div>
  </header>
   
</template>

<script>
export default {
    data(){
        return{
          /*   isOpen: false, */
          hover: false,
        }
    },

    methods: {
     /*  toggle () {
        this.isOpen = !this.isOpen
        console.log(this.toggle)

      } */
     /*  toggle: function(locale){
          console.log(locale)
           if(this.isOpen. !== locale) {
        this.isOpen.locale = locale;
      }
    }, */

    toggle: function(){

    } 

}
}

</script>

<style>
</style>