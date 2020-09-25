<template>
  <div id="app">
    <TimerList />
  </div>
</template>

<script>
import TimerList from '@/components/TimerList'

export default {
  name: 'App',
  components: {
    TimerList
  }
}
</script>

<style>
@import './fonts/fonts.css';

#app {
  font-family: 'Gotham Pro', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
