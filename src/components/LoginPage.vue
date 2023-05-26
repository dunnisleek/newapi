<template>
  <section>
    <div class="form-wrapper">
      <h2>welcome Back {{}}</h2>
      <div class="error-message" role="alert" v-if="error">{{ error }}</div>
      <form @submit.prevent="postData">
        <div>
          <label for="email" class="label">Your Email </label>
          <input
            type="text"
            id="text"
            placeholder="Email"
            v-model="email"
            required
          />
        </div>

        <div>
         
          <label for="password" class="label">Password</label>
          <!-- <input
            type="{{ showPassword ? 'text' : 'password' }}"
            placeholder="password"
            v-model="password"
            required
          /> -->

          <input v-if="showPassword" type="text" class="passwordinput"   placeholder="Password" v-model="password" />
           <input v-else type="password"  placeholder="password" v-model="password">
          <button @click="toggleShow()"  class="togglebtn">{{ showPassword ? 'Hide' : 'Show' }}</button>
        </div>

      
        <input class="submitbtn" type="submit" value="sign in" />
      </form>
    </div>
  </section>
</template>

<script>
import axios from "axios";

export default {
  name:'LoginPage',
  components: {},
  data() {
    return {
      email: "",
      password: "",
      error: "",
      showPassword:false
    };
  },
  computed: {
    buttonLabel() {
      return (this.showPassword) ? "Hide" : "Show";
    }
  },
  methods: {
    async postData() {
      try {
        let result = await axios.post(
          "https://dolphin-app-4xaig.ondigitalocean.app/v1/admin/login",
          {
            email: this.email,
            password: this.password,
          }
        );
        if (result) {
          this.$router.push({ name: "dashboard" });
        }
        console.warn(result);
      } catch (error) {
        this.error = "invalid username/password";
      }
    },
    toggleShow() {
      this.showPassword = !this.showPassword;
    }
  
  },
};
</script>

<style scoped>
section {
  background: #000000;
  height: 100vh;
  margin: 0px;
}

div.form-wrapper {
  position: relative;
  top: 150px;
  left: 0;
  right: 0;
  color: #fff;
  margin: 0 auto;
  max-width: 300px;
  background: #2c0000;
  border-radius: 24px;
  overflow: hidden;
  height: 50vh;
  padding: 02% 5% 5%;
  box-shadow: 0 5px 40px rgba(71, 107, 210, 0.19);
}
h2 {
  font-size: 25px;
  font-weight: 400;
  font-family: "DM Sans", sans-serif;
  text-align: center;
}
form {
  width: 200px;
  display: block;
  padding-top: 40px;
}
label {
  font-size: 0.85rem;
  display: block;
  margin-bottom: 8px;
  color: #fff;
  transition: 0.3s;
}
input {
  display: block;
  border-radius: 4px;
  border: 1px solid #9999bc;
  background: #f5f7fc;
  transition: 0.3s;
  height: 45px;
  padding: 2px 14px;
  outline: none;
  width: 280px;
  margin-bottom: 20px;
}
.submitbtn {
  background-color: #ee2525;
  border: none;
  margin-top: 20px;
  border-radius: 40px;
  color: #fff;
  font-size: 14px;
}
.submitbtn:hover {
  background-color: #f32d2dda;
  transition: all ease-in 0.3s;
}
.error-message {
  font-size: 16px;
  color: red;
  font-weight: 400;
}
.passwordinput{
  
}
.togglebtn{
    position: absolute;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    top: 284px;
    left: 328px;
    border:none;
    cursor: pointer;
}
</style>
