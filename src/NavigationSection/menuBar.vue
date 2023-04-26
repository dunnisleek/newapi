<template>
  <div class="menu">
    <div>
      <a href="/"> <img src="@/assets/acumenlogo.svg" /></a>
    </div>
    <div>
      <button class="redBtn" @click="getUsers">Refresh Data</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  
  data(){
    return{
        users:[]
    }
  },
  methods: {
    // this is to refresh the entire window or page
    // refreshPage() {
    //   window.location.reload();
    // },

    getUsers() {
      const URL = "https://restcountries.com/v3.1/all";
      axios.get(URL).then((res) => {
        // console.log(res.data)
        this.users = res.data;
        console.log("this is recall");
      });
    },
  },
};
</script>
<style scoped>
* {
  box-sizing: border-box;
  font-family: "DM Sans", sans-serif;
}
.menu {
  max-width: 100%;
  display: flex;
  justify-content: center;
  gap: 61rem;
  align-items: center;
  border-bottom: 1px solid #eaeaea;
  padding: 20px 0px;
}
.redBtn {
  background: #fb242a;
  border-radius: 50px;
  width: 190px;
  height: 44px;
  font-size: 18px;
  color: #fff;
  border: none;
}
</style>
