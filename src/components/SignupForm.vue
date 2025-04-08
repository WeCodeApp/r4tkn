<template>
    <form>
      <label for="email">Email</label>
      <input type="email" required v-model="email" />
  
      <label for="password">Password</label>
      <input type="password" required v-model="password" />
  
      <label>Roles:</label>
      <select v-model="role">
        <option value="---" default>Select role</option>
        <option value="developer">Web Dev</option>
        <option value="designer">Web Designer</option>
      </select>
  
      <div class="terms">
        <input type="checkbox" v-model="terms" required />
        <label>Accept Terms</label>
      </div>
  
      <label for="skills">Skills</label>
      <input type="text" v-model="tempSkill" @keyup="addSkill" />
  
    
      <div 
        v-for="(skill, index) in skills" 
        :key="index" 
        class="pill" 
        @click="removeSkill(index)"
      >
        {{ skill }}
      </div>
    </form>
  
    <p>Email : {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms: {{ terms }}</p>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        role: '',
        terms: false,
        tempSkill: '',
        skills: [],
      }
    },
    methods: {
      addSkill(e) {
       
        if (e.key === ',' && this.tempSkill) {
         
          const parsedSkill = this.tempSkill.slice(0, -1).trim()
         
          if (!this.skills.includes(parsedSkill)) {
            this.skills.push(parsedSkill)
          }
       
          this.tempSkill = ''
        }
      },
    
      removeSkill(index) {
        this.skills.splice(index, 1)
      },
    },
  }
  </script>
  
  <style>
  body {
    margin: 0;
    background: #eee;
  }
  
  form {
    max-width: 420px;
    margin: 30px auto;
    background: #555;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  
  input {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  
  /* New style for select element */
  select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
    background: #fff;
    margin-bottom: 20px;
    outline: none;
    -webkit-appearance: none; /* Removes default arrow in WebKit browsers */
    -moz-appearance: none; /* Removes default arrow in Firefox */
    appearance: none; /* Standardized property */
  }
  
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
  
  .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
  </style>
  