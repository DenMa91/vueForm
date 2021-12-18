<template>
 <SignUpForm/>
</template>

<script>

import SignUpForm from './components/SignUpForm.vue'

export default {
  name: 'App',
  components: { SignUpForm,  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
body{
  margin: 0;
  background-color: #eee;
}
</style>
