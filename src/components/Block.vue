<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click here {{delay}}
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return {
            showBlock:false,
            score:0,
            timer:null
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true;
            this.startTimer();
            
        },this.delay)
    },
    updated(){
        console.log("data updated");
    },
    unmounted(){
        console.log("component unmounted");
    },
    methods:{
        startTimer(){
           this.timer= setInterval(()=>{
               this.score +=50;
            },50)
        },
        stopTimer(){
            clearInterval(this.timer);
           // console.log(this.score);
            this.$emit("endGame",this.score)
        }
    }
}
</script>

<style>
 .block{
     width: 400px;
     height: 300px;
     cursor:pointer;
     background-color:aqua ;
     margin:20px auto;
     padding-top:30px;
 }
</style>