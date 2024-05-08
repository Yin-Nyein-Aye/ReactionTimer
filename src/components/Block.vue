<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            showBlock:false,
            score:0,
            timer:null
        }
    },
   mounted()
   {
        setTimeout(() => {
            this.showBlock=true,
            this.startTimer()
        },this.delay);
    },
    methods:{
        startTimer(){
            this.timer=setInterval(() => {
                this.score+=50; 
                console.log(this.timer);               
            }, 50);
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit("endGame",this.score)
        }
    }
    
}
</script>

<style>
.block{
    background: rgb(141, 40, 40);
    margin: 20px auto;
    width: 300px;
    height: 200px;
    padding-top: 30px;
    color:white;
}
</style>