<template>
  <div class="main">
  <form  @input.prevent>
    <h1>REGISTRATION</h1>
    <div class="content">
        <label for="username">Username</label>
        <input type="text" id="username" v-model="username" @input="checkName">
    </div>
    <p>{{ error.username }}</p>

    <div class="content">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="password" @input="checkPassword">
    </div>    
    <p>{{ error.password }}</p>

    <div class="content">
        <label for="eamil">Email:</label>
        <input type="email" id="email" v-model="email" @input="checkEmail">
    </div>
    <p>{{ error.email }}</p>
   

        <button @click="checkError">Submit</button>
  </form>
</div>
</template>

<script>
export default{
  data(){
    return {
      username: '',
      password: '',
      email:'',
      error:{
        username:'',
        password:'',
        email:''
      }
    }
  },
  methods:{
    checkName(){
      if(this.username.length<4){
         this.error.username='user name lower than 4 word';
      }else
      this.error.username='';
    },
    checkPassword(){
      if( /[A-Z]/.test(this.password) && /[a-z]/.test(this.password) && /[0-9]/.test(this.password) && /[^A-Za-z0-9]/.test(this.password) && this.password.length > 4 ){
        this.error.password='';
      }else{
      this.error.password='password mustbe at least 8 characters';
      }
    },
    checkEmail(){
      if(/\S+@\S+\.\S+/.test(this.email)){
        this.error.email=''
      }else
      this.error.email='Nor correct email';
    },
    checkError(){
      if(this.error.username=='' && this.error.password=='' && this.error.email==''){
        alert("Success");
        this.username ='';
        this.password='';
        this.email='';
      }else{
       alert('check inputs');
    }
  }
}
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.main{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: rgb(21,34,170);
  background: linear-gradient(135deg, rgba(21,34,170,1) 7%, rgba(238,141,30,1) 28%, rgba(191,16,31,1) 47%, rgba(242,255,14,1) 70%, rgba(109,10,121,1) 87%);
  height: 100vh;
}
form{
  background-color:gray;
  padding: 100px;
  border: none;
  outline: none;
  border-radius: 10%;
  text-align: center;
}
h1{
  color:gold;
  margin-bottom: 50px;
}
.content{
  display: flex;
  align-items: center;
  gap:30px;
  margin-bottom: 20px;
}
.content input{
  padding: 10px;
  border: none;
  outline: none;
  border-radius: 15px;
  width: 100%;
  background-color:darkcyan;
}
p{
  color: crimson;
  margin-bottom: 10px;
}

button{
  padding: 10px;
  outline: none;
  border: none;
  border-radius: 10px;
  background-color:gold;
  color: aliceblue;
  margin-top: 10px;
}

</style>
