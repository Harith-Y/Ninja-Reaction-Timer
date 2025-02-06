<template>
  <div class="block" v-if="showBlock">
    Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data () {
        return {
          showBlock: false
        }
    },
    mounted() {
      // console.log('Component mounted')
      setTimeout(() => {
          this.showBlock = true
          // console.log(this.delay)
      }, this.delay)
    },
    
    // updated() {
    //   console.log('Component updated')
    // },
    // unmounted() {
    //   console.log('Component unmounted')
    // }
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
    }
</style>