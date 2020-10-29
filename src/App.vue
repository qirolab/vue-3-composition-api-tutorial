<template>
  <div>
    <!-- <div>
      <TodosList />
    </div>

    <div>
      <TodosListV3 title="Composition API" />
    </div> -->

    <!-- <WatchExample /> -->
    <VModelsExample />
  </div>
</template>

<script>
// import TodosList from "./components/TodosList";
// import TodosListV3 from "./components/TodosListV3";
// import WatchExample from "./components/WatchExample";
import VModelsExample from "./components/v-models/VModelsExample";

export default {
  name: "App",
  components: {
    // TodosList,
    // TodosListV3,
    // WatchExample,
    VModelsExample,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  text-align: center;
}
</style>
