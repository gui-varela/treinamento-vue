<template>
  <div id="container">

    <header id="logo" class="flex-row">
      <img src="./assets/check.png" alt="logo">
      <h1 id="logotipo">Checklist</h1>
    </header>

    <form @submit.prevent="addCheck(check)" id="inputs" class="flex-row">
      <input type="text" name="" id="" placeholder="Crie uma tarefa..." v-model="check.title">
      <button type="submit">Criar</button>
    </form>

    <div id="checklist" class="flex-column">
      <div v-for="c in checks" :key="c.id" class="flex-column">
        <hr>
        <div class="tarefa flex-row">
          <div id="item" class="flex-row">
            <input type="checkbox" name="" id="" class="checkbox" v-model="c.checked">
            <h2 class="unchecked" v-if="!c.checked">{{ c.title }}</h2>
            <h2 class="checked" v-else>{{ c.title }}</h2>
          </div>
          
          <img height="30" src="./assets/trash.svg" alt="">
        </div>
      </div>
    </div>
  
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return { 
      checks: [],
      check: {
        checked: false
      }
    }
  },
  methods: {
    addCheck(check) {
      check.id = Date.now();
      this.checks.push(check);
      this.check = { checked: false }
    }
  }
}
</script>

<style>
#app {
  font-family: Source-Sans, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Source Sans Pro', sans-serif;

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  background-color: #f2f2f2;
}

.flex-row {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: row;
}

.flex-column {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

#container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

#logo {
  margin: 60px;
}

#logo > img {
  height: 50px;
  margin-right: 15px;
}

#logo > h1 {
  font-size: 40px;
  font-family: 'Roboto Mono', monospace;
  font-weight: bolder;
  color: #2c3e50;
}

form#inputs {
  margin: 30px 0;
  width: 500px;
}

#inputs > input {
  height: 40px;
  width: 250px;
  margin-right: 10px;
  padding-left: 13px;
  color: #333;
  font-size: 12pt;
  border: none;
  border-radius: 15px;
  outline: none;
  box-shadow: 0 7px 10px #00000010;
}

#input-item::placeholder {
  color: #888;
  font-size: 10pt;
  font-style: italic;
}

#input-item:focus {
  border: 1px solid #4488dd;
}

#inputs > button {
  width: 90px;
  height: 40px;
  
  border-radius: 15px;
  border: none;
  box-shadow: 0 7px 10px #00000010;
  color: #fff;
  font-weight: bolder;
  font-family: 'Source Sans Pro', sans-serif;
  font-size: 12pt;
  background: #44dd88;
  transition: 300ms;
}

#inputs > button:hover {
  background: #32c760;
  cursor: pointer;
}

#checklist {
  margin: 30px 0;
}

.tarefa {
  width: 500px;
  justify-content: space-between;
}

.checkbox {
  margin-right: 15px;
}

.tarefa h2 {
  font-weight: 400;
}

.tarefa h2.unchecked {
  color: #333;
}

.tarefa h2.checked {
  color: #888;
  text-decoration: line-through;
  font-style: italic;
}

hr {
  border: none;
  border-top: 1px solid #ccc;
  width: 500px;
  margin: 15px 0;
}
</style>
