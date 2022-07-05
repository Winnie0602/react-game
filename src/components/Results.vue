<template>
  <p>您的反應時間： {{ score }} 毫秒</p>
  <p class="comment">{{ comment }}</p>
</template>

<script>
export default {
    name:'Results',
    props: ['score'],
    data(){
        return{
            comment: null
        }
    },
    mounted(){
        if ( this.score < 250 ){
            this.comment = '太厲害了！叫你第一名！'
        } else if ( this.score < 400 ){
            this.comment = '眼明手快，反應還不錯唷～'
        } else {
            this.comment = '還不夠快，再回去練練吧～'
        }
    }
}
</script>

<style scoped>
.comment{
    color:red
}
</style>