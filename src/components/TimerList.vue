<template>
  <div class='timerlist'>
    <Timer v-bind:timer='timer' v-for='timer in timerList' :key='timer.id'/>
    <NewTimer v-bind:timerList='timerList'/>
  </div>
</template>



<script>
import Timer from '@/components/Timer'
import NewTimer from '@/components/NewTimer'

export default {
  name: 'TimerList',
  components: {
    Timer,
    NewTimer
  },
  data() {
    return {
      timerList: [
        {seconds: 35, minutes: 0, hours: 0},
        {seconds: 35, minutes: 20, hours: 0},
        {seconds: 35, minutes: 20, hours: 1}
      ]
    }
  }
}
</script>

<style scoped>
  .timerlist {
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    width: 775px;
  }

  @media (min-width: 768px) and (max-width: 1023px) {
    .timerlist {
      width: 500px;
    }
  }
  @media (min-width: 320px) and (max-width: 767px) {
    .timerlist {
      width: 225px;
    }
  }
</style>
