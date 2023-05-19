<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    }, 
    // LIFECYCLE COMPONENTS - WILL INTERACT W/VUE ELEMENTS AT DIFFERENT POINTS
    mounted() {
        // console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true 
            this.startTimer()
        }, this.delay)
    },
    // Start timer here
    updated() {
        // console.log('component updated!')
    },
    unmounted() {
        // console.log('unmounted')
    },
    methods: {
        // Get total time of the program running (userTime = timer - delay)
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },

        // Ends reaction timer (userTime = stopTimer_time - delay)
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
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
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>