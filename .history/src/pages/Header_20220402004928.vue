
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.6/js/materialize.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/1.0.26/vue.js"></script>


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
           <div id="app">

  <button @click="show = !show">Toggle v-if</button>
  <button @click="rebindDropdown">Rebind Dropdown</button>
   
  <div v-if="show">
    <!-- Dropdown Trigger -->
    <a class='dropdown-button btn' href='#' data-activates='dropdown1'>Drop Me!</a>

    <!-- Dropdown Structure -->
    <ul id='dropdown1' class='dropdown-content'>
      <li><a href="#!">one</a></li>
      <li><a href="#!">two</a></li>
      <li><a href="#!">three</a></li>
    </ul>
  </div>

</div>


           <!--   <a class='dropdown-trigger btn' href='#' data-target='dropdown1' @click= "toggle" >Rapport</a>
                <ul id='dropdown1' class='dropdown-content' v-if="isOpen">
                    <li><a href="#!">Reception</a></li>
                    <li class="divider" tabindex="-1"></li>
                    <li><a href="#!">Distribution</a></li>
                </ul>    -->
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

  data: {
    show: true
  },
  
  methods: {
    rebindDropdown: function() {
      $('.dropdown-button').dropdown();  
    }
  },
  
  ready: function() {
    $('.dropdown-button').dropdown();  
  }

}
</script>

<style>
</style>