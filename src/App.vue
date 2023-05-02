<template>
  <div>
    <menuBar />
    <dashBoard></dashBoard>
    <router-view/>
    <!-- <TableView /> -->
  </div>
</template>

<script>
// import ActiveOrder from './components/ActiveOrder.vue';
// import TableView from "./components/TableView.vue";
import DashBoard from "./components/DashBoard.vue";
import menuBar from "./NavigationSection/menuBar.vue";

// import addPost from './components/addPost.vue';

export default {
  name: "App",
  components: {
    // TableView,
    DashBoard,
    menuBar,
  },
  data() {
    return {};
  },
};
</script>

<style>
#app {
  font-family: "DM Sans", sans-serif;

  margin-bottom: 200px;
}
</style>
