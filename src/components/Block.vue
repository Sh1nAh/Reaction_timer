<template>
    <div class="block" v-if="showBlock" @click="stopTimer">Click here</div>
</template>

<script>
import { onUnmounted } from 'vue'
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            score: 0,
            timer: null
        }
    },
    // lifecycle hooks
    mounted() {
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer()
        }, this.delay)
    },
    // updated() {
    //     console.log('data updated')
    // },
    // unmounted() {
    //     console.log('component unmounted')
    // },
    methods: {
        startTimer() {
            this.timer=setInterval(() => {
                this.score+=50;
            }, 50)
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit('endGame', this.score)
        }
    }
}
</script>

<style>
    .block {
        background-color: #7532a2;
        color: #fff;
        width: 300px;
        height: 200px;
        margin: 20px auto;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>