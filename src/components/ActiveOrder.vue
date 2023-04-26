<template>
  <section>
    <!-- <div><menuBar /></div> -->
    <!-- start of userlists -->
    <div class="backbtn">
      <button class="redBtn" @click="goBack">Back</button>
    </div>
    <div class="wrapper">
      <!-- <div class="tab"> -->
      <div class="tab">
        <h3
          class="bluebg"
          :class="{ active: !isActive }"
          @click="display(0), (isActive = !isActive)"
        >
          <span class="circlee"></span>
          Ventures ({{ ventureCount }})
        </h3>

        <!-- inner Userlists pages -->
        <div class="userlist" v-if="currentStep === 0">
          <table>
            <tbody>
              <tr v-for="(userList, index) in users" :key="index">
                <td>{{ userList.name.official }}</td>
                <td>{{ userList.name.common }}</td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="userlistdigital" v-else-if="currentStep === 1">
          <table>
            <tbody>
              <tr v-for="(userList, index) in users" :key="index">
                <td>{{ userList.name.official }}</td>
                <td>{{ userList.name.common }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="userlistcommunity" v-else-if="currentStep === 2">
          <table>
            <tbody>
              <tr v-for="(userList, index) in users" :key="index">
                <td>{{ userList.name.official }}</td>
                <td>{{ userList.name.common }}</td>
              </tr>
            </tbody>
          </table>
        </div>

        <h3
          :class="{ active: isActive }"
          @click="display(1), isActive == !isActive"
        >
          <span class="pinkcircle"></span>Digital ({{ digitalCount }})
        </h3>

        <h3 @click="display(2)">
          <span class="purplecircle"></span>Community ({{ communityCount }})
        </h3>
      </div>

      <!-- start of form -->
      <div class="innerdetail">
        <!-- <div > -->

        <div class="Fcircle">
          <h2><span class="circle"> Favour</span></h2>

          <p>{{ currentDate }} ({{ currentTime }})</p>
        </div>
        <!-- details -->
        <h2 class="title">Name <br /><span>Favour</span></h2>
        <h2 class="title">
          Email <br />
          <span style="text-decoration: underline"> favour@acumen.digital</span>
        </h2>
        <h2 class="title">
          Message<br />
          <span class="para">
            Hello my dear,How are you? Abeg I want to to do mobile app
            Thanks.</span
          >
        </h2>
      </div>
    </div>
  </section>
</template>

<script>
// import menuBar from "@/NavigationSection/menuBar.vue";
import moment from "moment-timezone";
import { createRouter, createWebHistory } from "vue-router";

const router = createRouter({
  history: createWebHistory(),
  routes: [],
});

export default {
  name: "ActiveOrder",
  props: {
    users: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      ventureCount: 20,
      digitalCount: 95,
      communityCount: 107,
      currentStep: 0,
      isActive: false,
      currentTime: "",
      // toggle: false,
    };
  },
  // day: "numeric",
  // inject: ["users", "message"],
  computed: {
    currentDate() {
      const date = new Date();
      const options = { month: "long", weekday: "long" };
      return date.toLocaleDateString(undefined, options);
    },
  },
  mounted() {
    moment.tz.setDefault("Africa/Lagos");
    const nowInLagos = moment.tz("Africa/Lagos");
    this.currentTime = nowInLagos.format("h:mm a");
  },
  methods: {
    display(val) {
      this.currentStep = val;
    },

    goBack() {
      router.go(0); // Go back one page in the history
    },
  },
};
</script>
<style scoped>
section {
  position: relative;
  height: 150vh;
  top: 0;
  bottom: 0;
}

.circle::before {
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #d3fff4;
  margin-right: 37px;
  position: relative;
  top: 0.3rem;
  /* top: 2px; */
}
.circlee::before {
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #d3fff4;
  margin-right: 7px;
  position: relative;
  top: 0.3rem;
}
.pinkcircle::before {
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #ffdede;
  margin-right: 7px;
  position: relative;
  top: 0.3rem;
  /* top: 2px; */
}
.purplecircle::before {
  background-color: #ccd9ff;
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin-right: 7px;
  position: relative;
  top: 0.3rem;
}

h3 {
  font-family: DM Sans;
  font-size: 16px;
  font-weight: 400;
  line-height: 24px;
  letter-spacing: 0px;

  text-align: center;
  /* margin-right: 20px; */
  height: 40px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 170px;
}
h3:hover {
  background: #e8e8e8;
  height: 40px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;

  /* width: 170px; */
}
.active {
  background-color: #e8e8e8;
}
.wrapper {
  padding: 40px;
  display: flex;
  max-width: 92%;
  justify-content: space-evenly;
  flex-wrap: nowrap;
  gap: 2rem;
  align-content: center;
  margin: 0 auto;
  width: 1331px;
}
.backbtn {
  width: 1331px;
  margin: 0 auto;
}
.tab {
  position: relative;
  display: flex;

  border: 1px solid #dadada;
  border-radius: 24px;
  padding: 30px;
  width: 50%;
  height: 70vh;
  /* height: 45vh; */
}
.innerdetail {
  width: 45%;
  border: 1px solid #dadada;
  position: relative;
  border-radius: 24px;
  padding: 30px;
  padding-right: 150px;
}
.title {
  font-size: 16px;
  line-height: 24px;
  padding-bottom: 12px;
  font-weight: 700;
}
.title span {
  font-size: 18px;
  line-height: 28px;
  font-weight: 400;
}
.para span {
  width: 30px;
  padding: 100px;
}
.bluebg {
  /* background: #e8e8e8; */
  height: 40px;
  /* width:150px; */
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.Fcircle {
  display: flex;
  justify-content: space-between;
  background: #fdfdfd;

  padding: 2px 10px;
  border-radius: 24px;
}
.Fcircle h2 {
  font-size: 17px;
  font-weight: 300;
}
.userlist {
  position: absolute;
  top: 100px;
  left: 60px;
  right: 20px;
  /* left:140px; */
  /* bottom: 100px; */
  /* max-width: 70%; */
}
.userlistdigital {
  position: absolute;
  top: 100px;
  left: 60px;
  right: 20px;
  /* bottom: 100px; */
  /* max-width: 70%; */
}
.userlistcommunity {
  position: absolute;
  top: 100px;
  left: 60px;
  right: 20px;
  bottom: 100px;
}

tr::before {
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #d3fff4;
  margin-right: 37px;

  position: relative;
  top: 1.3rem;
}
tbody tr:nth-of-type(even):before {
  background-color: #ffdede;
}
tbody tr:nth-of-type(odd):before {
  background-color: #d3fff4;
}
td {
  width: 700px;
  padding-right: 0px;
  /* padding-bottom: 50px; */
  /* height:10vh; */
}
tr {
  cursor: pointer;
  background: #fdfdfd;
  height: 8vh;
}
table {
  border-collapse: initial;
  border-spacing: 0 30px;
}
.redBtn {
  background: #d3fff4;
  border-radius: 50px;
  padding: 12px;
  /* width: 190px; */
  /* height: 44px; */
  font-size: 15px;
  color: #000000;
  border: none;
  position: relative;
  top: 14px;
  left: 5px;
}
</style>
