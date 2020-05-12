<template>
  <div>
    <div class="align-center margins">
      <img src="../assets/logo.svg" class="logo" alt="Logo Minhas Finanças" />
      <h1 class="align-center">Minhas Finanças</h1>
    </div>
    <register-finance @create-finance="createFinance" @import-finances="importFinances"></register-finance>
    <table class="table margins">
      <thead>
        <tr>
          <th class="width">Item</th>
          <th class="width">Data</th>
          <th class="width">#</th>
          <th class="width">$</th>
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
      return date
        .split("-")
        .reverse()
        .join("-");
    },
    importFinances(finances) {
      finances.forEach(finance => {
        this.finances.push({
          item: finance.item,
          date: finance.data,
          quantity: finance.quantidade,
          value: finance.valor
        });
      });
      console.log(this.finances);
    }
  }
};
</script>

<style scoped>
.body {
  width: 40%;
  margin: 0px auto;
  font-family: tahoma;
  color: #282828;
}

.align-center {
  text-align: center;
}

label {
  font-size: 16px;
}

.logo {
  width: 72px;
  height: 72px;
  margin: 0px auto;
}

.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}

button {
  margin-top: 30px;
  border: none;
  background-color: #1e95ea;
  color: white;
  height: 40px;
  width: 100px;
  font-size: 14px;
}

.form {
  width: 100%;
  padding: 20px;
  border: 1px solid #d8d8d8;
}

input {
  width: 96%;
  height: 25px;
  margin-bottom: 20px;
  padding: 5px;
  border-radius: 5px;
  box-shadow: inset 0px 0px 0px 0px;
  font-size: 14px;
  margin-top: 10px;
}
.btn {
  margin: 0px auto;
}

.margins {
  margin: 20px 0px;
}

.table {
    width: 100%
}

.width {
    text-align: left;
    width: 25%
}
</style>
