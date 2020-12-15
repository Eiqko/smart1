<template>
 <div id="app" class="q-pa-md q-gutter-sm">
   <h1>data di console</h1>
  <form ref="form" @submit.prevent="submit">
    <input type="text" name="phone type" placeholder="type of phone...">
    <input type="number" name="quantity" placeholder="quantity">
    <button type="submit">Submit</button>
  </form>
     <q-btn color="purple" label="Purple" aria-placeholder="quasar not working becuase i create it with vue cli not with quasar cli, because run of time i just send this, thanks"/>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  components: {
    
  },
   methods: {
    submit: function () {
      const formDat = new FormData(this.$refs['form']); 
      const data = {}; 
      for (let [key, val] of formDat.entries()) {
        Object.assign(data, { [key]: val })
      }
      console.log(data);
      axios.post('https://jsonplaceholder.typicode.com/posts', data)
        .then(res => console.log(res.request.response))
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
body{
 background: #c94064;
}

input{
  margin-left: 8px;
  margin-right: 8px;
  border: 1px solid gray;
  border-radius: 10px;
  padding: 10px;
}

button{
  border-radius: 10px;
  padding: 10px;
   border: 1px solid rgb(230, 96, 136);
  color: black;
  background: #ce0e41;
  cursor: pointer;
}
button:hover{
  background: #e97695;
}
input:focus,
select:focus,
textarea:focus,
button:focus {
    outline: none;
}
</style>
