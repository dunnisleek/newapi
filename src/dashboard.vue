<template>
       <div>
         <menuBar />
         
         <TableView />
         
       </div>
     </template>
     
     <script>
   
     import TableView from "./components/TableView.vue";
     
     import menuBar from "./NavigationSection/menuBar.vue";
 
     
     export default {
       name: "App",
       components: {
         TableView,
         menuBar
       },
       data() {
         return {};
       },
     };
     </script>
     <style scoped>
     div{
      padding-bottom: 6rem;
     }
     </style>
     