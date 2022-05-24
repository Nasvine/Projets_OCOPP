<template>
    <footer class="page-footer" style="background-color: #1BA8A8; font-family: inherit;">
    
        <ul class="foot" >
          <li >
            <a href="">Mentions légales</a> 
          </li>
          <li >
            <a href="" style="border-left:1px solid #fff">Connectez-vous</a> 
          </li>
          <li >
            <a href="" style="border-left:1px solid #fff">A propos</a>
          </li>
        </ul>
      
    <div class="row valign-wrapper">
            <div class="col s6 offset-s3 valign">
            <div class=" small  center-align">
                <p>Copyright © 2022-Tous droits réservés</p>
            </div>
        </div>
    </div>
        
</footer>

</template>

<script>
export default {
    setup() {
        
    },
}
</script>

<style>
  footer{
    background-color: #1BA8A8;
    
  }
  .foot{
    background-color: #1BA8A8;
    height: 20px;
    display: flex;
    padding: 0;
    justify-content: center;
  }
  .foot li{
    list-style-type: none;
  }
  .foot a{
    color: #fff;
    display: block;
    margin-left: 0.7rem;
    /* padding: 0.4rem 0; */
    text-align: center;
    padding-left: 0.7rem;

  }
  
  .valign-wrapper{
      padding-bottom: 20px;
      background-color: #1BA8A8;
      color: #fff;
      height: 20px;
      display: -webkit-flex;
      display: -ms-flexbox;
      display: flex;
      -webkit-align-items: center;
      -ms-flex-align: center;
      align-items: center;
  }

</style>