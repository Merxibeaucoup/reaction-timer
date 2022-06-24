<template>

<div class="resultsBlock">
<p>Reaction Time - {{score}} ms</p>
<p class="rank">
    {{message}}
</p>
</div>
  
</template>

<script>
export default {

    // props from App Vue 
    props:['score'],

    data(){
        return{
            // initialize Rank to null , which when true, prints out a message after the game 
            message: null
        }
    },

    // display the message using the mounted Hook
    // Uses the score prop to mount 
    mounted(){

        // basic object oriented programming here 
        if ( this.score < 250){
            this.message = 'Ninja Fingaz!'
        } else if(this.score < 400) {
            this.message = 'Rapid reflex!'
        }
        else{
            this.message = '_._._._slow as a snail!'
        }
    }

}
</script>

<style>

.resultsBlock{
     width:400px;
    border-radius: 20px;
    background: #020202;
    color: burlywood;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

.rank{
    font-size: 1.4em;
    color:aqua;
    font-weight: bold;
    
}

</style>