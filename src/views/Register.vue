<template>
  <div class="register">
    <div class="">
      <div class="col-md-6 offset-md-3">
        <h2 class="display-4 text-center mt-5">Tester L'application</h2>
        <h3 class="display-4 text-center mt-5">Créer votre compte </h3>
        <form action="#">
            <div class="mb-3">
            <label for="name" class="form-label">Name</label>
            <input type="string" v-model="name" class="form-control" id="name"/>
          </div>
          <div class="mb-3">
            <label for="email" class="form-label">Email</label>
            <input type="email" v-model="email" class="form-control" id="email"/>
          </div>
          <div class="mb-3">
            <label for="password" class="form-label" >Password</label>
            <input type="password" v-model="password" class="form-control" id="password"/>
          </div>
         <div class="mb-3">
            <label for="password_confirmation" class="form-label" >Confirmer Password</label>
            <input type="password" v-model="password_confirmation" class="form-control" id="password_confirmation"/>
          </div>

          <div style="color: red" v-if="error">{{ error }}</div>

          <button type="submit" class="btn btn-primary"  @click="performRegister">S'inscrire</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>


import axios from 'axios';

export default {
    name: "login" , 
    data(){
        return{
            name:'',
            email :'',
            password : '',
            password_confirmation:'',
            error : '',
        }
    },
    methods:{
        performRegister(){
          axios.post('http://localhost:8000/api/auth/register',{
            name: this.name,  
            email: this.email,
            password: this.password,
            password_confirmation: this.password_confirmation,
          })
          .then(res =>{
            console.log(res.data);
             const token = localStorage.setItem('token',res.access_token)
             const user = localStorage.setItem('user',res.data.user)
            //this.$router.push('/profile');
            console.log(token);
            console.log(user);
           window.location.href = "http://localhost:8000";
          })
          .catch(err =>{
            console.log(err.message);
            this.error = err.message;
          })
            //console.log("perform login");
            
        }
    }

};
</script>
