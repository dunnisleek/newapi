<template>
  <section>

  <div class="wrap">
  <div>
    <div class="subdetails">
       <div> <h3 class="recent">Most Recent Entries</h3></div>
        <div>
          <h3 class="bluebg">
            <span class="circle"></span>
                Ventures
            
          </h3>
         
         <h3><span class="pinkcircle"></span>Digital</h3> 
         <h3><span class="purplecircle"></span>Community</h3> 
        </div>
        <!-- <button class="redBtn" @click="changeUserName()">Refresh Data</button> -->
    </div> 
    
  <!-- <div> -->
   
     
   <table>
     
       
       <tbody>
      
         <tr v-for="(user, index) in users" :key="index" @click="openComponent(index)">
          
            <!-- <td v-text="user.name" class="cell1" ></td> -->
            <td  class="cell1" >{{user.name}}</td>
             <td class="cell">{{user.created_at}}</td>
             <td class="cellTwo">{{user.email}}</td>
             
         
        </tr>
       </tbody>
    </table>
  <!-- </div> -->
 
</div>
</div>
<div class="activeSection">
 
  <active-order v-if="isComponentOpen" :users="users"></active-order>
  <dash-board :users="users"></dash-board>

</div>

</section>

</template>


<script>

import DashBoard from './DashBoard.vue';
import ActiveOrder from './ActiveOrder.vue';
import axios from 'axios'

  // async function getCountries() {
  //       const promise = await fetch("https://restcountries.com/v3.1/all");
  //       const data = await promise.json();
  //       console.log(data);
  //     }
  //     getCountries();
export default {
  el:"#app",
  components:{ActiveOrder, DashBoard},
  
    data(){
      return{
        message:'helo',
        users:[],
        isComponentOpen: false,
        activeIndex: null,
     
      }
     
    },

   methods:{
     
       getUsers(){
        const URL = "https://dolphin-app-4xaig.ondigitalocean.app/v1/contact/";
        axios
        .get(URL)
        .then(res => {
          console.log(res.data)
          this.users = res.data.data.slice(0,5)
          console.log('this is recall')
        })

      },
      openComponent(index) {
      this.isComponentOpen = !this.isComponentOpen;
     
      this.activeIndex = index;
    },
    changeUserName() {
      this.message = 'Data has been refreshed!';
      this.$forceUpdate();
    }
  
  },
 
    mounted(){
     
      this.getUsers();
  
  
    },
    
  //   provide() {
  //   return {
  //     message: 'Hello from parent table',
    
  //   }

  // }
}
</script>
<style scoped>

.wrap{
  border: 1px solid #C4C4C4;
  border-radius:20px;
  top:4rem; 
  position: relative;
  padding:80px 60px 40px 60px ;

  max-width: 1200px;
  margin: 0 auto;

  /* height: 100vh;
   */
}


.subdetails{
  display:flex;
  width:100%;
  justify-content: space-between;
}
.subdetails div:nth-child(2){
  display:flex;
}

.circle::before {
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color:  #D3FFF4;
  margin-right: 7px;
  position: relative;
  top: 0.3rem;
  /* top: 2px; */
}
.pinkcircle::before{
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color:   #FFDEDE;
  margin-right: 7px;
  position: relative;
  top: 0.3rem;
  /* top: 2px; */
}
.purplecircle::before{
  background-color:#CCD9FF;
  content: "";
  display: inline-block;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin-right: 7px;
  position: relative;
  top: 0.3rem;
}
h3{

  margin-top:-30px;
  font-family: DM Sans;
font-size: 16px;
font-weight: 400;
line-height: 24px;
letter-spacing: 0px;
text-align: left;
margin-right: 20px;

}
.recent {
 font-family: DM Sans;
font-size: 24px;
font-weight: 400;
line-height: 24px;
letter-spacing: 0px;
text-align: left;

}


tr::before{
  content: "";
  display:inline-block;
  width:20px;
  max-width: 20px;
  height: 20px;
  /* max-height: 20px; */
  border-radius: 50%;
  background-color:  #D3FFF4;
  margin-right: 17px;
  position: relative;
 top:1.5rem;
  text-align: center;
  /* top: 0.5rem; */
 
}
tbody tr:nth-of-type(even):before {
  background-color: #FFDEDE;
}
tbody tr:nth-of-type(odd):before {
  background-color: #D3FFF4;
}
.cell{
  padding-left: 15rem;
 
}
.cellTwo{
  padding-left: 15rem;
}
.cell1{
  padding-left: 3rem;
  
}
div .activeSection{
  position: absolute;
  top:0;
  left:0;
  right:0;
  margin-top: 6rem;
 background: white;
}
tr{
  cursor: pointer;
  /* margin-bottom: 30px; */
  background: #FDFDFD;
  /* padding-left: 20px; */
  border-radius: 20px;
  background: #FDFDFD ;
  height:8vh;

 
}
table{
  font-size:18px;
  margin-bottom: 0px;
  padding-bottom: 0px;
  height:10vh;
  border-collapse:initial;
  border-spacing: 0 10px;
  
}


</style>