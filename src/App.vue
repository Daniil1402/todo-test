<template>
  <div id="app">
    <MainTemplate/>
    
  </div>
</template>

<script>
import MainTemplate from '@/components/MainTemplate.vue'


export default {
  name: 'App',
  components: {
    MainTemplate
  }
}
</script>

<style>
body {
  background: rgba(0, 0, 0, 0.3);
}

a:active,
a:focus,
button:active,
button:focus,
form:active,
form:focus,
textarea:active,
textarea:focus {
  box-shadow: none;
  outline: none;
}

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  color: #525252;
}

.container {
  max-width: 1600px;
  width: 100%;
  margin: 0 auto;
}

.title {
  margin-bottom: 15px;
  text-align: center;
}
</style>
