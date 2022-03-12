<template>
  <div class="container" @submit.prevent>
    <form class="card">
      <h1>CV for Vue Developer!</h1>
      <AppInput
         placeholder="Enter Name"
         :error="errors.name"
         label="What's your name?"
         v-model="name"
      />

      <div class="form-control">
        <label for="age">Choose age</label>
        <input
            type="number"
            id="age"
            max="70"
            v-model.number="age"
        >
      </div>

      <div class="form-control">
        <label for="city">Your city</label>
        <select id="city" v-model="city">
          <option value="tbs">Tbilisi</option>
          <option value="btm">Batumi</option>
          <option value="gr">Gori</option>
          <option selected value="zgd">Zugdidi</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Up for relocation?</span>
        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="Yes"/> Yes</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="No"/> No</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">What you know in Vue?</span>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="Vuex"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="Vue CLI"/> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="Vue Router"/> Vue Router</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Company rules</span>
        <div class="checkbox">
          <label><input type="checkbox" v-model='agree'>Agree</label>
        </div>
      </div>

      <button type="submit" class="btn primary" @click="submitHandler">Send</button>
    </form>
  </div>
</template>

<script>
import AppInput from "./AppInput";
  export default {
    data(){
      return{
        name: '',
        age: 23,
        city: 'zgd',
        relocate: null,
        skills: [],
        agree: false,
        errors: {
          name: null
        }
      }
    },
    components:{
     AppInput
    },
    methods: {
      formIsvalid(){
        let isValid= true
        if(this.name.length === 0){
          this.errors.name = 'Name is empty'
         isValid = false
        } else{
          this.errors.name = null
        }

        return isValid
      },
       submitHandler(){
         if(this.formIsvalid()){
           console.group()
           console.log('Name:', this.name)
           console.log('age:', this.age)
           console.log('city:',  this.city)
           console.log('relocate:',  this.relocate)
           console.log('skills:', this.skills)
           console.log('agree:', this.agree)
           console.groupEnd()
         }

       }
    }
  }
</script>

<style>
 small{
   color: #e53935;
   font-weight: bold;
 }
 .form-control.invalid input{
   border-color: #e53935;
 }
</style>
