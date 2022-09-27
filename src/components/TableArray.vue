<template>
  <div class="table_row">
    <div class="row">{{row_data.date}}</div>
    <div class="row">{{row_data.name}}</div>
    <div class="row">{{row_data.count}}</div>
    <div class="row">{{row_data.distance}}</div>
  </div>
</template>

<script>
export default {
  name: "TableArray",
  props: {
   row_data: {
     type: Object,
     default: () => {
       return {}
     }
   }
  }
}
</script>

<style>
  .table_row {
    display: flex;
    justify-content: space-around;
    flex-basis: 25%;
  }
  .row {
    flex-basis: 25%;
    text-align: center;
  }
</style>