<template>
  <form @submit.prevent="validateForm" class="signupform">
    <div>
      <label>Email:</label>
      <input type="Email" v-model="email" @input="validateEmail" />
      <span class="error" v-if="mailError">{{ mailError }}</span>
    </div>
    <div>
      <label>password:</label>
      <input type="password" v-model="password" @input="validatePassword" />
      <span v-if="passwordError" class="error">{{ passwordError }}</span>
    </div>
    <div>
      <label>phonenumber:</label>
      <input type="phonenumber" required v-model="phonenumber"  @input="validatePhoneNumber"/>
      <span class="error" v-if="phoneNumberError">{{ phoneNumberError }}</span>
    </div>
    <label>Role:</label>
    <select class="selector">
      <option value="developer">Web Dev</option>
      <option value="Designer">Web Designer</option>
    </select>
    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="AddSkills" />
    <div class="terms">
      <div v-for="skill in skills" :key="skill" class="pill">
        <span @click="deleteSkill(skill)">
          {{ skill }}
        </span>
      </div>
      <div>
        <input type="checkbox" reauired />
        <label>Accept terms and Conditions</label>
      </div>
    </div>
    <div class="submit">
      <button>Create Account</button>
    </div>
  </form>
  <!-- <p> this is the list of the skills {{ skills }}</p> -->
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      phonenumber: "",
      role: "",
      skills: [],
      tempSkill: "",
      passwordError: "",
      phoneNumberError: "",
      mailError: "",
    };
  },
  methods: {
    AddSkills(e) {
      if (e.key === ",") {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },
    validateEmail() {
      const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
      if (!this.email) {
        this.mailError = "email is required";
      } else if (!emailPattern.test(this.email)) {
        this.mailError = "please enter a valid form of mail";
      } else {
        this.mailError = "";
      }
    },
    validatePassword() {
      this.passwordError =
        this.password.length > 5 ? "" : "password must be at least 6 char long";
    },
    validatePhoneNumber() {
      const phonePattern = /^\+?[0-9\s()-]{7,15}$/;
      if (!this.phonenumber) {
        this.phoneNumberError = "entering a phone number is required";
      } else if (!phonePattern.test(this.phonenumber)) {
        this.phoneNumberError = "enter a valid phone number";
      } else {
        this.phoneNumberError = "";
      }
    },
    validateForm() {
      this.validateEmail();
      this.validatePassword();
      this.validatePhoneNumber();
      if (
        this.validateEmail &&
        this.validatePassword &&
        this.validatePhoneNumber
      ) {
        alert("From submited successfully");
      }
    },
    //this is working with indexes
    // DeleteSkill(index) {
    //   this.skills.splice(index, 1);
    // },
    deleteSkill(skill) {
      // this works filtering the items the item i clicked on its deleted
      this.skills = this.skills.filter((item) => {
        // filter here is passing by the ellements if an ellement is same as the ellement is the condition its moved off
        return skill !== item; // if this is false the item is deleted and the new array si created without this ellement
      });
    },
  },
  setup() {
    return {};
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background-color: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
  box-shadow: 0 5px 10px lightgrey;
}
label {
  color: lightgrey;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6 em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid lightgrey;
  color: gray;
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
  background-color: #eee;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
  border-radius: 20px;
}
button {
  background-color: lightseagreen;
  border: 0;
  padding: 15px 20px;
  box-shadow: 0 5px 10px lightgray;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.submit {
  text-align: center;
}
.error {
  color: red;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
