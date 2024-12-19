<template>
    <form class="signupform">
        <label>Email:</label>
        <input type="Email" required v-model="email">

        <label>password:</label>
        <input type="password" required v-model="password">
        
        <label>phonenumber:</label>
        <input type="phonenumber" required v-model="phonenumber">
        
        <label>Role:</label>
        <select class="selector">
            <option value="developer">Web Dev</option>
            <option value="Designer">Web Designer</option>
        </select>

        <div class="terms">
            <input type="checkbox" reauired>
            <label>Accept terms and Conditions</label>
        </div>
        
    </form>
</template>

<script>
export default {
    data() {
        return {
            email:'',
            password:'',
            phonenumber:'',
            role:'',
        }
    },
    setup () {
        

        return {}
    }
}
</script>

<style>
   
  form{
    max-width: 420px;
    margin: 30px auto;
    background-color: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0 5px 10px lightgrey;
  }
  label{
     color: lightgrey;
     display: inline-block;
     margin: 25px 0 15px;
     font-size: 0.6 em;
     text-transform: uppercase;
     letter-spacing: 1px;
     font-weight: bold;
  }
  input ,select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid lightgrey;
    color: gray;
  }
  input[type='checkbox']{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0 ;
    position: relative;
    top: 2px;
  }
</style>