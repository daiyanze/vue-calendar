<template>
  <div id="app">
    <h1>vue-event-calendar</h1>
    <h2 class="t-center">Default template</h2>
    <vue-calendar
      @day-changed="handleDayChanged"
      @month-changed="handleMonthChanged"
    ></vue-calendar>
  </div>
</template>

<script>
let today = new Date()
export default {
  name: 'app',
  methods: {
    handleDayChanged (data) {
    },
    handleMonthChanged (data) {
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 30px;
}

h1, h2, h3 {
  font-weight: normal;
  margin: 0;
  padding: 0;
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
.t-center{
  text-align: center;
  margin: 20px;
}
</style>
