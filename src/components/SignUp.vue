<template>
  <form @submit.prevent="submit">
    <label >Name</label>
    <input type="name" v-model="name">
    <div v-if="errMsg" class="error"><p>{{errMsg}}</p></div>

    <label >Email</label>
    <input type="email" v-model="email">

    <label >Password</label>
    <input type="password" v-model="password">

    <select v-model="role">
        <option value="Developer">Web Developer</option>
        <option value="Designer">Web Designer</option>
  </select>

  <div>
    <label for="">Skills</label>
    <input type="text" @keyup.alt="addSkills" v-model="skill">
  </div>

  <div v-for="skill in skills" :key="skill">
    <p>{{skill}} <span class="cross" @click="deleteSkill(skill)">&#x2716;</span></p>

  
  </div>

  <div>
    <input type="checkbox" v-model="accept">
    <label for="">Accept Terms and conditions</label>
  </div>

  <div class="align">
    <button class="create">Submit Form</button>
  </div>

  <!-- <hr>

  <div>
    <input type="checkbox" value="HTML" v-model="skills">
    <label for="">HTML</label>
  </div>

  <div>
    <input type="checkbox" value="CSS" v-model="skills">
    <label for="">CSS</label>
  </div>

  <div>
    <input type="checkbox" value="Javascript" v-model="skills">
    <label for="">Javascript</label>
  </div>

<div>
    <input type="checkbox" value="PHP" v-model="skills">
    <label for="">PHP</label>
  </div> -->

</form>

  <p>{{name}}</p>
  <p>{{email}}</p>
  <p>{{password}}</p>
  <p>{{role}}</p>
  <p>accept-{{accept}}</p>
  <p>skills-{{skills}}</p>
</template>

<script>
export default {
    data(){
        return{
            name:"",
            email:"",
            password:"",
            role:"Developer",
            accept:false,
            skills:[],
            skill:"",
            errMsg:""
        }
    },
    methods:{
        addSkills(e){
            if (e.key==="," && this.skill){
           this.skills.push(this.skill);
            this.skill=""
            }
        },
        deleteSkill(skill){
            this.skills=this.skills.filter(loopSkill=>{
              return loopSkill != skill;
            })
         
        },
        submit(){
          if (!this.name){
            this.errMsg="Name can't be empty!";
          }
        }

   }

}
    
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label {
    color: black;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input,select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
.cross{
  color: crimson;
  cursor: pointer;
}
.create{
  background-color: royalblue;
  padding: 8px;
  color: white;
  border-radius: 10px;
}
.align{
  text-align: center;
}
.error{
  color: crimson;
}
</style>