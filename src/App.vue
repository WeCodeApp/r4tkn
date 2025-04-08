

<template>
  <SignupForm />
</template>


<script>
import SignupForm from './components/SignupForm.vue'

export default{
  name: 'App',
  components:{
    SignupForm
  }
}


</script>


<style>
#app{
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  text-align:center;
  color: black;
  margin-top: 60px;

}


body {
  margin: 0;
  background: #eee;
}

</style>
