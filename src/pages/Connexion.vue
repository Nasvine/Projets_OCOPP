<template>
    <section class="back">
        <div class="row valign-wrapper">
            <div class="col s6 offset-s3 valign">
                <div class=" small white  center-align">
                    <div class="card-conexion-logo">
                        <div class="logo">
                            <figure>
                                <img src="../logo.png" alt="">
                            </figure>
                        </div>
                    </div>
                    <div class="row">
                        <form class="col s12" @submit.prevent="handleSubmit">
                            <div class="row">
                                <div class="input-field col s12">
                                    <input id="email" type="email" class="validate" v-model="email">
                                    <label for="email">Email</label>
                                </div>
                            </div>
                            <div class="row">
                                <div class="input-field col s12">
                                    <input type="password" id="password" class="validate" v-model="password">
                                    <label for="password">Password</label>
                                </div>
                            </div>
                            <div>
                                <button class="waves-effets #1a237e indigo darken-4 btn-large">Connexion</button>
                            </div>

                        </form>
                    </div>

                </div>
            </div>
        </div>

    </section>
</template>

<script>
import axios from 'axios';
export default {
    name: "Login",
    data() {
        return {
            email: null,
            password: null,
            tab: []
        }
    },
    methods: {
        async handleSubmit(){
            console.log(this.email+" "+this.password);

           const response = await axios.post('http://api.odoo.ocoop.rintio.com/odoo/api/v1.0/users/login',{
                    email: this.email,
                    password: this.password,
              });
            /* console.log(response.data.company_id); */
            if(response.status == 200)
        {
            localStorage.setItem( "users",JSON.stringify((response.data.company_id).replace(/[^0-9]/g,"" )));
            this.$router.push({path:'/'})
        }
        console.warn(response)
              
        },
        
    }

}
</script>

<style >
.back {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
}
</style>
