<template>
    <div class="menu-items" @click="isOpen = !isOpen">
        <a href="#" class="waves-effect waves-light btn-small">
            {{title}}
        </a>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="10">
        <path fill="#FFF" d="M0 0h24v24H0z"/>
        <path d="M12 8l6 6H6z"/></svg>
        <transition name="fade" appear>
        <div class="sub-menu" v-if="isOpen">
            <div>
              <a href="/Rapport-reception" style="color:#fff;">Reception</a> <br>
              <a href="/Rapport-distribution" style="color:#fff;">Distribution</a>
            </div>
        </div>
        </transition>
    </div>
</template>

<script>
export default {
 
      name: "Dropdown",
      props:['title', 'items'],
      data(){
          return{
              isOpen:false
          }
      }
  
}
</script>

<style>
.menu-items .sub-menu{
    position: relative;
    padding: 6px;
    padding-left: 10px;
    text-decoration-color: white;
    background-color:#1BA8A8;
    top: calc(100% +10px);
    left: 40%;
    transform: translateX(-50%);
    margin-left: 5px;
    border-radius: 0px 0px 2px 2px;
    width: 87%;
}
  
</style>
