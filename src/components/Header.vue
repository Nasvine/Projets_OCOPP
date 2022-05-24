<template>
  <header>
    <div class="nav-wrapper">
      <div class="row">
        <div class="level col s12">
          <div
            class="col s2"
            style="display: flex; justify-content: flex-start"
          >
            <div class="logo">
              <figure>
                <img src="../logo.png" alt="" height="100px" />
              </figure>
            </div>
          </div>
          <div class="col s4"></div>

          <div
            class="col s6"
            style="display: flex; justify-content: flex-end; margin-top: 50px"
          >
            <div class="col menu-items">
              <a class="waves-effect waves-light btn-small" href="/Reception"
                >Reception</a
              >
            </div>
            <div class="col menu-items">
              <a class="waves-effect waves-light btn-small" href="/Distribution"
                >Distribution</a
              >
            </div>

            <div class="col menu-items">
              <Dropdown title="Rapport" :items="Rapport" />
            </div>

            <div class="col menu-items">
              <a class="waves-effect waves-light btn-small" href="/Contact"
                >Contactez-nous</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Dropdown from "../components/Dropdown.vue";

export default {
  metaInfo: {
    title: "Header",
  },
  data() {
    return {
      Rapport: [
        {
          title: "Reception",
          link: "/Rapport-reception/",
        },
        {
          title: "Distribution",
          link: "/Rapport-distribution/",
        },
      ],
    };
  },
  components: {
    Dropdown,
  },

  methods: {
    toggle() {
      this.isOpen = !this.isOpen;
      console.log(this.toggle);
    },
    /*  toggle: function(locale){
          console.log(locale)
           if(this.isOpen. !== locale) {
        this.isOpen.locale = locale;
      }
    }, */

    /* toggle: function(){

    }  */
  },
};
</script>

<style>
header {
  /* position: relative; */
  /*  padding-top: 50px; */
  width: 100%;
  background-color: #fff;
}
</style>