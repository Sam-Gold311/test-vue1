<template>
  <div class='timer'>
    <div class='timer__time'>
      <span v-if='timer.hours'>{{ timer.hours + ':' }}</span><span v-if='timer.minutes || timer.hours'>{{ timer.minutes + ':' }}</span><span>{{ timer.seconds }}</span>
    </div>
    <hr class='timer__line'>
    <div class='timer__buttons'>
      <i @click='timerPlayPause' class='material-icons'>{{ playbutton }}</i>
      <i @click='timerStop' class='material-icons'>stop</i>
    </div>
  </div>
</template>


<script>
export default {
  name: 'Timer',
  props: ['timer'],
  data() {
    return {
      playbutton: 'play_arrow',
      timerId: ''
    }
  },
  methods: {
    timerPlayPause() {
      if (this.playbutton === 'play_arrow') {
        this.playbutton = 'pause';
        this.$el.style.color = '#fff';
        this.$el.getElementsByClassName('timer__line')[0].style.background = '#fff';
        this.timerId = setInterval(function(){
          this.timer.seconds += 1;
          if (this.timer.seconds === 60) {
            this.timer.seconds = 0;
            this.timer.minutes += 1;
          }
          if (this.timer.minutes === 60) {
            this.timer.minutes = 0;
            this.timer.hours += 1;
          }
        }.bind(this), 1000)
      } else {
        this.playbutton = 'play_arrow';
        this.$el.style.color = '#9E9E9E';
        this.$el.getElementsByClassName('timer__line')[0].style.background = '#9E9E9E';
        clearInterval(this.timerId);
      }
    },
    timerStop() {
      if (this.playbutton === 'pause') {
        this.playbutton = 'play_arrow';
        this.playbutton = 'play_arrow';
        this.$el.style.color = '#9E9E9E';
        this.$el.getElementsByClassName('timer__line')[0].style.background = '#9E9E9E';
        clearInterval(this.timerId);
      }
      this.timer.hours = this.timer.minutes = this.timer.seconds = 0;
    }
  }
}

</script>

<style lang='scss' scoped>
  .timer {
    font-size: 22px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 225px;
    height: 120px;
    background: #696969;
    color: #9E9E9E;
    box-sizing: content-box;
    &:not(:nth-child(3n)) {
      margin-right: 50px;
    }
    &:not(:last-child) {
      margin-bottom: 45px;
    }
    &__line {
      margin: 20px 0;
      height: 1px;
      border: none;
      background: #9E9E9E;
      width: 100%;
    }
    &__buttons {
      display: flex;
      align-self: center;
      justify-content: space-between;
      width: 85px;
      & i {
        cursor: pointer;
        font-size: 28px;
      }
    }
  }

  @media (min-width: 768px) and (max-width: 1023px) {
    .timer:not(:nth-child(3n)) {
      margin-right: 0;
    }
    .timer:not(:nth-child(2n)) {
      margin-right: 50px;
    }
  }

  @media (min-width: 320px) and (max-width: 767px) {
    .timer:not(:nth-child(3n)) {
      margin-right: 0;
    }
    .timer:not(:nth-child(2n)) {
      margin-right: 0;
    }
  }
</style>
