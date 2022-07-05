<template>
    <div class="block" v-if="showBlock" @click="stopTimer" >
        <p>Click Me !</p>
    </div>
</template>

<script>
export default {
    name:'Block',
    props:['delay'],
    data(){
        return{
            showBlock : false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        } , this.delay )
    },
    methods:{
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            } , 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('endGame',this.reactionTime)
        }
    }
}
</script>

<style scoped>
.block {
    width:300px;
    height: 250px;
    background-color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    color: pink;
    font-size:1.5rem;
    font-weight: 700;
    border: 5px solid pink;
    border-radius: 1rem;
}
</style>