<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <div class="block-title">Click Block</div>
    <div class="block-content">Click Me</div>
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data () {
        return {
          showBlock: false,
          timer: null,
          reactionTime: 0
        }
    },
    mounted() {
      // console.log('Component mounted')
      setTimeout(() => {
          this.showBlock = true
          this.startTimer()
          // console.log(this.delay)
      }, this.delay)
    },
    methods: {
      startTimer() {
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10)
      },
      stopTimer() {
        clearInterval(this.timer)
        console.log("Your reaction time is: ", this.reactionTime, "ms")
        this.$emit('stop', this.reactionTime)
      }
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        padding: 100px 0;
        text-align: center;
        margin: 40px auto;
        transition: background-color 0.5s;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    .block:hover {
        background-color: #0a8f6a;
    }

    .block-title {
        font-size: 2em;
        margin-bottom: 20px;
    }

    .block-content {
        font-size: 1.2em;
        margin-bottom: 20px;
    }

</style>