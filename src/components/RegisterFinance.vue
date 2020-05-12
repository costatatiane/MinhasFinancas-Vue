<template>
  <div>
    <button type="button" id="btn-import" v-on:click="importFinances">Importar</button>
    <form @submit.prevent="onSubmit">
      <p>
        <label for="item">Item:</label>
        <input id="item" v-model="item" type="text" placeholder="Item" />
      </p>

      <p>
        <label for="date">Data:</label>
        <input id="date" v-model="date" type="date" placeholder="dd/mm/aaaa" />
      </p>

      <p>
        <label for="quantity">Quantidade:</label>
        <input id="quantity" v-model="quantity" type="number" placeholder="00" />
      </p>

      <p>
        <label for="value">Valor:</label>
        <input id="value" v-model="value" type="number" placeholder="00.00" />
      </p>

      <p>
        <input type="submit" value="Incluir" />
      </p>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "RegisterFinance",
  props: {
    msg: String
  },
  data() {
    return {
      item: null,
      date: null,
      quantity: null,
      value: null,
      errors: [],
    };
  },
  methods: {
    onSubmit() {
      this.errors = [];
      if (this.item && this.date && this.quantity && this.value) {
        let finance = {
          item: this.item,
          date: this.date,
          quantity: this.quantity,
          value: this.value
        };
        this.$emit("create-finance", finance);
        (this.item = null),
          (this.date = null),
          (this.quantity = null),
          (this.value = null);
      } else {
        if (!this.item) this.errors.push("Item obrigatório");
        if (!this.date) this.errors.push("Data obrigatório");
        if (!this.quantity) this.errors.push("Quantidade obrigatório");
        if (!this.value) this.errors.push("Valor obrigatório");
      }
    },
    importFinances() {
      let finances;
      axios
        .get("https://evening-badlands-20922.herokuapp.com/financas/semana")
        .then(response => {
          finances = response.data;
          this.$emit("import-finances", finances);
        })
        .catch(e => {
          this.erros.push(e);
        });
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
