<template>
  <div id="app" class="body">
    <finances></finances>
  </div>
</template>

<script>
import Finances from './components/Finances.vue'

export default {
  name: 'App',
  components: {
    finances: Finances,
  }
}
</script>

<style>
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
