

<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.6/js/materialize.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/1.0.26/vue.js"></script>

<template>

<div id="app">
<link href="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.6/css/materialize.css" rel="stylesheet"/>
  <button @click="show = !show">Toggle v-if</button>
   
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
    

</template>

<script>
export default{
    data(){
        return{
          show: false,
        }
    },
    
    watch: {
      show: function() {
        console.log('The value for "show" has changed. Rebinding dropdown...');
        $('.dropdown-button').dropdown();
      }
    },
    
    ready: function() {
      $('.dropdown-button').dropdown();  
    }
}
</script>