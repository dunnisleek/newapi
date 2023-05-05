<template>
       <div>
         <menuBar />
         <dashBoard></dashBoard>
         <TableView />
         
       </div>
     </template>
     
     <script>
   
     import TableView from "./components/TableView.vue";
     import DashBoard from "./components/DashBoard.vue";
     import menuBar from "./NavigationSection/menuBar.vue";
 
     
     export default {
       name: "App",
       components: {
         TableView,
         DashBoard,
         menuBar
       },
       data() {
         return {};
       },
     };
     </script>
     <style scoped>
     div{
      padding-bottom: 130px;
     }
     </style>
     