<template>
   <div class="container" v-if="showBlock">
      <div class="cube" @click="stopTimer">
          <div class="side front">Click Here</div>
          <div class="side back">Click Here </div>
          <div class="side right">Click Here </div>
          <div class="side left">Click Here </div>
          <div class="side top">Click Here </div>
          <div class="side bottom">Click Here </div>
      </div>
  </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
      return{
        showBlock:false,
        timer: null,
        score: 0
      }
    },
    mounted(){
      setTimeout(()=>{
        this.showBlock=true;
        this.startTimer();
      },this.delay)
    },
    methods:{
      startTimer(){
        this.timer=setInterval(()=>{
          this.score+=50;
        },50)   
      },
      stopTimer(){
        clearInterval(this.timer);
        this.$emit("endGame",this.score);
      }
    },
    
}
</script>

<style>
    .container {
  perspective: 800px;
  transform-style: preserve-3d;
}

.cube {
  width: 200px;
  height: 200px;
  position: relative;
  transform: rotateY(-45deg);
  transform-style: preserve-3d;
  animation: rotate-cube 4s linear infinite;
  margin: 80px auto;
}

.side {
  position: absolute;
  width: 200px;
  height: 200px;
  border: 2px solid black;
  text-align: center;
  font-size: 24px;
  line-height: 200px;
  font-weight: bold;
  background-color: green;
  color: white;
}

.front {
  transform: translateZ(100px);
}

.back {
  transform: translateZ(-100px) rotateY(180deg);
}

.right {
  transform: rotateY(90deg) translateZ(100px);
}

.left {
  transform: rotateY(-90deg) translateZ(100px);
}

.top {
  transform: rotateX(90deg) translateZ(100px);
}

.bottom {
  transform: rotateX(-90deg) translateZ(100px);
}

@keyframes rotate-cube {
  0% { transform: rotateY(0deg); }
  100% { transform: rotateY(360deg); }
}

</style>