<template>
  <div id="app">
    <div>
      <label>phone</label>
      <input type="text" v-model="phone"/>
      <button v-on:click="submit()">Submit</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default  {
  name: 'App',
  methods: {
    data() {
      return {
        phone: '',
      }
    },
    submit() {
     let url = "http://localhost:8080/api/bot/phone"
      axios.post(url, {"text":this.phone},{
      }).then(response => {
        console.log(response)
        setTimeout(this.requestData, 1000)
      }, response => {
        // error callback
        console.log(response.data)
      })
    }
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
