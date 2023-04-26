<template>
  <section>
    <div>
      <div class="userdetails" >
        <div><h3>Hello Ayo</h3></div>
        <div>
          <p>
            <b>{{ currentDate }}</b> <br />
            <span class="time">{{ currentTime }} in lagos</span>
          </p>
        </div>
      </div>

      <div class="contentBox">
        <div class="ventureBox" @click="showComponentB()">
          <h2>Ventures</h2>

          <p>{{ ventureCount }}</p>
        </div>

        <div class="digitalBox" @click="showComponentB()">
          <h2>Digital</h2>
          <p>{{ digitalCount }}</p>
        </div>
        <div class="communityBox"  @click="showComponentB()">
          <h2>Community</h2>
          <p>{{ communityCount }}</p>
        </div>
      </div>
      <div class="activeSection">
        <active-order
          v-if="componentToShow"
          :users="users"
        ></active-order>
      
      </div>
    </div>
  </section>
</template>

<script>
import ActiveOrder from "./ActiveOrder.vue";
import moment from "moment-timezone";
export default {
  components: { ActiveOrder },
  props: {
    users: {
      type: Array,
      required: true,
    }
  },
 
  data() {
    return {
      ventureCount: 87,
      digitalCount: 87,
      communityCount: 20,
      currentTime: "",
      componentToShow: false,
      

  
    };
  },
  methods: {
    showComponentB() {
      this.componentToShow = "ActiveOrder";
    }
  
  },

  computed: {
    currentDate() {
      const date = new Date();
      const options = { month: "long", day: "numeric", weekday: "long" };
      return date.toLocaleDateString(undefined, options);
    },
  },
  mounted() {
    moment.tz.setDefault("Africa/Lagos");
    const nowInLagos = moment.tz("Africa/Lagos");
    this.currentTime = nowInLagos.format("h:mm A");
  },
};
</script>

<style scoped>
/* *{
  box-sizing: border-box;
  font-family: 'DM Sans', sans-serif;
}
 .menu{
    max-width: 100%;
    display:flex;
    justify-content: center;
    gap:60rem;
    align-items: center;
    border-bottom: 1px solid #EAEAEA;
    padding:20px 0px;
   
 } */
.redBtn {
  background: #fb242a;
  border-radius: 50px;
  width: 190px;
  height: 44px;
  font-size: 18px;
  color: #fff;
  border: none;
}
.userdetails {
  max-width: 100%;
  display: flex;
  justify-content: center;
  gap: 67.5rem;
  align-items: center;
  margin: 0 auto;
 
 position: relative;
 
  /* gap:60rem; */
  /* gap:69rem;   */
  padding-top: 30px;
}
.userdetails h3 {
  font-weight: 300;
}
.contentBox {
  position: relative;
  display: flex;
  justify-content: space-around;
  gap: 1rem;
  align-items: center;
  align-content: center;
  margin: 0 auto;
  /* width: 90%; */
  max-width: 1324px;
  top: 2rem;
  bottom: 3rem;
}
.ventureBox {
  background: rgba(235, 255, 250, 1);
  font-weight: 400;
  width: 400px;
  height: 125px;
  border: 1px solid #000000;
  border-radius: 24px;
  padding: 10px 25px;
  position: relative;
  left: 0;
  cursor: pointer;
  /* flex:1; */
}
.ventureBox h2,
.digitalBox h2,
.communityBox h2 {
  font-size: 20px;
  line-height: 30px;
  font-weight: 400;
}
.ventureBox p {
  position: relative;
  font-size: 34px;
  line-height: 38px;
  margin-left: 20rem;
  /* left:20.5rem; */
  bottom: 0rem;
}
.digitalBox {
  background: #ffeded;
  width: 400px;
  height: 125px;
  border: 1px solid #000000;
  border-radius: 24px;
  padding: 10px 25px;
  cursor: pointer;
}

.digitalBox p,
.communityBox p {
  position: relative;
  font-size: 34px;
  line-height: 38px;
  margin-left: 20rem;
  bottom: 0rem;
}
.communityBox {
  background: #e9eeff;
  width: 400px;
  height: 125px;
  border: 1px solid #000000;
  border-radius: 24px;
  padding: 10px 25px;
}
.time {
  font-size: 14px;
  margin-left: 20px;
}
div .activeSection {
  position: relative;
  top: -300px;
  left: 0;
  right: 0;
  margin-top: 3rem;
  background: #ffffff;
  z-index: 8;
}
</style>
