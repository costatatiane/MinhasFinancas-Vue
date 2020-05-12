<template>
  <div>
    <register-finance @create-finance="createFinance" @import-finances="importFinances"></register-finance>
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
          <td>{{finance.date}}</td>
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
    },
    importFinances(finances) {
        finances.forEach(finance => {
            this.finances.push({          
                item: finance.item,
                date: finance.data,
                quantity: finance.quantidade,
                value: finance.valor})
        });
        console.log(this.finances);
    },
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
