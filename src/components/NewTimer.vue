<template>
  <div class='new-timer'>
    <i @click='addTimer' class='material-icons'>add</i>
  </div>
</template>


<script>
export default {
  name: 'NewTimer',
  props: ['timerList'],
  methods: {
    addTimer() {
     this.timerList.push({seconds: 0, minutes: 0, hours: 0})
   }
  }
}
</script>

<style lang='scss' scoped>
  .new-timer {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 225px;
    height: 120px;
    background: #696969;
    color: #9e9e9e;
    & i {
      cursor: pointer;
      font-size: 28px;
    }
  }
</style>
