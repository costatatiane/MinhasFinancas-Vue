<template>
  <div>
    <register-finance @create-finance="createFinance"></register-finance>
    <table class="table">
      <thead>
        <tr>
          <th>Item</th>
          <th>Data</th>
          <th>#</th>
          <th>$</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="finance in this.finances" :key="finance.item">
          <td>{{finance.item}}</td>
          <td>{{dateToText(finance.date)}}</td>
          <td>{{finance.quantity}}</td>
          <td>{{finance.value}}</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td></td>
        </tr>
      </tfoot>
    </table>
  </div>
</template>

<script>
import RegisterFinance from "./RegisterFinance";

export default {
  name: "Finances",
  components: {
    "register-finance": RegisterFinance
  },
  data() {
    return {
      finances: []
    };
  },
  methods: {
    createFinance(finance) {
      this.finances.push(finance);
    },
    dateToText(date) {
        return date.split('-').reverse().join('-');
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
