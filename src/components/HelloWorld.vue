<template>
  <form @submit.prevent="create">
    
    <label for="email">email</label>
    <input type="email" required v-model="email">

    <label>Password</label>
    <input type="password" v-model="password">
    <p v-if="err">{{err}}</p>

    <label for="">Role</label>
    <select v-model="role">
      <option value="developer">Web developer</option>
      <option value="desginer">Web desginer</option>
    </select>
    <!-- single checkbox -->
    <div>
      <input type="checkbox" v-model="accept">
      <label for="">accept terms and conditions</label>
    </div>
      <!-- multiple checkbox
    <label for="">name</label>
    <div>
      <input type="checkbox" value="id1" v-model="name">
      <label for="">accept terms and conditions</label>
    </div>
    <div>
      <input type="checkbox" value="id2" v-model="name">
      <label for="">accept terms and conditions</label>
    </div>
    <div>
      <input type="checkbox" value="id3" v-model="name">
      <label for="">accept terms and conditions</label>
    </div> -->

    <div>
      <label for="">skills</label>
      <input type="text" @keyup.alt="addskill" v-model="skill">
    </div>
    <div v-for="skill in skills" :key="skill">
      <p>{{skill}} <span @click="remove(skill)" class="icon">&#x2716;</span></p>
    </div>
    <div class="crdiv">
      <button class="create">Create</button>
    </div>
    
    

  </form>
  

</template>

<script>
export default {
    data(){
      return{
        email:"",
        password:"",
        role:"developer",
        accept:false,
        name:[],
        skills:[],
        skill:"",
        err:"",
      }
    },
    methods:{
      addskill(event){
        if(event.key===","){
            this.skills.push(this.skill);
            this.skill=""
        }
      },
      remove(skill){
        this.skills=this.skills.filter(loopskill=>{
          return loopskill!=skill
        })
      },
      create(){
        
        if(this.password.length<8){
          this.err ="at least 8 password"
        }
      }
    }
}
</script>

<style>
form{
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label{
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input{
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid rgb(109, 108, 108);
  color:rgb(131, 127, 127);
}
select{
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid rgb(109, 108, 108);
  background-color:rgb(131, 127, 127);
  color: white;
  text-transform: uppercase;
}
input[type="checkbox"]{
  
  width: 16px;
  display: inline-block;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.icon{
  cursor: pointer;
  color: red;
}
.create{
  padding: 6px 40px;
  border-radius: 10px;
  margin: 20px auto;
} 
.crdiv{
  text-align: center;
}

</style>