<template>
  <signupform/>
</template>

<script>
import signupform from './components/SignUpForm.vue'
export default {
  name:'app',
  components:{
    signupform
  },
 
}
</script>

<style>
#app{
  font-family: Arial, Helvetica, sans-serif ;
  text-align: center;
  margin-top: 60px;
}
body{
  margin: 0;
}
</style>