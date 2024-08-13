<template>
  <router-view />
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body{
  padding: 0;
  margin: 0;
}

.logo {
    width: 200px;
}

.register input, .login input, .add input {
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    border: 1px solid skyblue;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
}

.register button, .login button, .add button {
    width: 320px;
    height: 40px;
    background-color: skyblue;
    color: white;
    border: 1px solid skyblue;
    cursor: pointer;
    text-align: center;
    transition: background-color 0.3s ease;
}

.custom-button {
    background-color: #3498db;
    color: white;
    padding: 4px 5px;
    border: none;
    margin-left: 5px;
    border-radius: 5px;
    font-size: 14px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.custom-button:hover {
    background-color: #2980b9;
    transform: scale(1.05);
}

.custom-button:active {
    background-color: #1c5d8d;
    transform: scale(0.95);
}

.custom-button:focus {
    outline: none;
    box-shadow: 0 0 5px #2980b9;
}

</style>
