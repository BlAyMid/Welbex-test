<template>
<!--  <div>-->
<!--    <select>                      //сначала хотел сделать такой вариант, но увидел более интересный и попробовал его реализовать                   --> 
<!--      <option>Название</option>-->
<!--      <option>Количество</option>-->
<!--      <option>Расстояние</option>-->
<!--    </select>-->
<!--    <select>-->
<!--      <option>Равно</option>-->
<!--      <option>Содержит</option>-->
<!--      <option>Больше</option>-->
<!--      <option>Меньше</option>-->
<!--    </select>-->
<!--    <input type="text" id="myInput" placeholder="Search">-->
<!--  </div>-->
  <div class="table">
    <div class="table_header">
      <p @click="sortByDate">date
        <svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24"><path d="M0 0h24v24H0z" fill="none"/><path d="M12 5.83L15.17 9l1.41-1.41L12 3 7.41 7.59 8.83 9 12 5.83zm0 12.34L8.83 15l-1.41 1.41L12 21l4.59-4.59L15.17 15 12 18.17z"/></svg>
      </p>
      <p @click="sortByName">name
        <svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24"><path d="M0 0h24v24H0z" fill="none"/><path d="M12 5.83L15.17 9l1.41-1.41L12 3 7.41 7.59 8.83 9 12 5.83zm0 12.34L8.83 15l-1.41 1.41L12 21l4.59-4.59L15.17 15 12 18.17z"/></svg>
      </p>
      <p @click="sortByCount">count
        <svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24"><path d="M0 0h24v24H0z" fill="none"/><path d="M12 5.83L15.17 9l1.41-1.41L12 3 7.41 7.59 8.83 9 12 5.83zm0 12.34L8.83 15l-1.41 1.41L12 21l4.59-4.59L15.17 15 12 18.17z"/></svg>
      </p>
      <p @click="sortByDistance">distance
        <svg xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24"><path d="M0 0h24v24H0z" fill="none"/><path d="M12 5.83L15.17 9l1.41-1.41L12 3 7.41 7.59 8.83 9 12 5.83zm0 12.34L8.83 15l-1.41 1.41L12 21l4.59-4.59L15.17 15 12 18.17z"/></svg>
      </p>
    </div>
    <table-array
      v-for="row in table_data"
      :key="row.id"
      :row_data="row"
    />
<!--    <div class="table-pagination">--> <!--Попытка реализации пагинации, не нашёл ошибку, но думаю, что ошибка в преобразовании данных-->
<!--      <div class="page"-->
<!--        v-for="page in pages"-->
<!--        :key="page"-->
<!--        @click="pageClick(page)"-->
<!--      >{{page}}</div>-->
<!--    </div>-->
  </div>
</template>

<script>
import TableArray from "@/components/TableArray";
export default {
  components: {TableArray},
  name: "TableGeneration",
  props: {
    table_data: {
      type: Array,
      default: () => {
        return []
      }
    }
  },
  data() {
    return {
      // tablePerPage: 10,
      // pageNumber: 1
    }
  },
  computed: {
   // pages() {
   //    return Math.ceil(this.table_data.length / 10);
   // },
   //  paginated() {
   //   let from = (this.pageNumber - 1) * this.tablePerPage;
   //   let to = from + this.tablePerPage;
   //   return this.table_data.slice(from,to);
   //  }
  },
  methods:{
    sortByDate() {
      // eslint-disable-next-line vue/no-mutating-props
      this.table_data.sort((a, b) => a.date.localeCompare(b.date))
    },
    sortByName() {
      // eslint-disable-next-line vue/no-mutating-props
      this.table_data.sort((a, b) => a.name.localeCompare(b.name))
    },
    sortByCount() {
      // eslint-disable-next-line vue/no-mutating-props
      this.table_data.sort((a, b) => a.count - b.count)
    },
    sortByDistance() {
      // eslint-disable-next-line vue/no-mutating-props
      this.table_data.sort((a, b) => a.distance - b.distance)
    },
    // pageClick(page) {
    //   this.pageNumber = page;
    // }
  }
}

</script>

<style>
  .table {
    max-width: 900px;
    margin: 0 auto;
  }
  .table_header {
    display: flex;
    justify-content: space-around;
    border-bottom: solid 1px black;
  }
  .table_header p {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-basis: 25%;
    text-align: left;
    cursor: pointer;
  }

  /*.table-pagination {*/
  /*  display: flex;*/
  /*  flex-wrap: wrap;*/
  /*  justify-content: center;*/

  /*}*/
  /*.page {*/
  /*  padding: 8px;*/
  /*  border: solid 1px black;*/
  /*  margin-top: 30px;*/
  /*  margin-right: 10px;*/
  /*}*/
  /*.page:hover {*/
  /*  background-color: blue;*/
  /*  cursor: pointer;*/
  /*  color: white;*/
  /*}*/
</style>
