<template>

<!--Only displays if show block is true-->
<div class="block" v-if="showBlock" @click="stopTimer">
    Click Me 
</div>
  
</template>

<script>
export default {
// delay props from APP vue 
    props: ['delay'],

data(){
    return{
        // initialize showBlock
        showBlock: false,
        //initialize timer ;; stores a set interval (timer runs in 10 ms steps)
        timer: null,
        //initialize Reaction time
        reactionTime:0
    }

},

// start the timer in the mounted Hook
// mounts the component using the delay prop
// mount is a LifeCycle Hook
    mounted(){  

        //  set showBlock to true 
        //set timeout waits a certain amount of time using the delay prop before  we change a property (ie showBlock)
        setTimeout(()=>{
            this.showBlock = true
            // showBlock true( appears) then the timer starts right away !
            this.startTimer()
        }, this.delay)
    }, 
    methods:{
        // should be called soon as the block component appears
        startTimer(){
            // setinterval function is gonna run every 10 miliSeconds at a time
                this.timer = setInterval(()=> {

                     // after every 10 miliSeconds add 10 ms to reaction timer
            this.reactionTime +=10

                }, 10)
           
        }, 

        // gets called when the user clicks on the block during paly
        stopTimer(){
            //clear interval when timer is stopped
            clearInterval(this.timer)
            // passes the stopTimer method  as @end to the parent component .. together with the reactiontime(data)
            this.$emit('end', this.reactionTime)
        }
    }
    

}
</script>

<style>
.block{
    width:400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>