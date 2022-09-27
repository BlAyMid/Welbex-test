<template>
  <div id="app">
  </div>
  <table-generation
    :table_data = TABLE
  />
</template>

<script>
import TableGeneration from "@/components/TableGeneration";
import axios from "axios";



export default {
  name: 'App',
  components: {
    TableGeneration
  },
  data: () => {
    return {
      TABLE: Array
    };
  },
  mounted() {
    axios
        .get('http://localhost:3000/table')
        .then(response => (this.TABLE = response.data));
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
