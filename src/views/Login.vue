<template>
  <div class="login">
    <div class="">
      <div class="col-md-6 offset-md-3">
        <h2 class="display-4 text-center mt-5">Se Connecter</h2>
        <form action="#">
          <div class="mb-3">
            <label for="email" class="form-label">Email</label>
            <input type="email" v-model="email" class="form-control" id="email"/>
          </div>
          <div class="mb-3">
            <label for="password" class="form-label" >Password</label>
            <input type="password" v-model="password" class="form-control" id="password"/>
          </div>

          <div style="color: red" v-if="error">{{ error }}</div>

          <button type="submit" class="btn btn-primary"  @click="performLogin">Sign In</button>
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
            email :'',
            password : '',
            error : '',
        }
    },
    methods:{
        performLogin(){
          axios.post('http://localhost:8000/api/auth/login',{
            email: this.email,
            password: this.password,
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
