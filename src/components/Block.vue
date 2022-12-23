<template>
    <div class="block" v-if="showBlock" @click="stopPlaying">
        <p>Click me</p>
    </div>
</template>

<script>
    export default{
        props:['delay'],
        data(){
            return {
                showBlock: false,
                timer:null,
                reactionTime: 0,
            }
        },
        mounted(){
            setTimeout(()=>{
                this.showBlock = true;
                this.timer = setInterval(()=>{
                    this.reactionTime += 10;
                },10);
                
            },this.delay);
        },
        methods:{
            stopPlaying(){
                clearInterval(this.timer);
                this.$emit('end',this.reactionTime);
            }
        },
    }
</script>

<style>
    .block{
        width: 150px;
        height: 120px;
        line-height: 120px;
        background: lightgreen;
        border-radius: 10px;
        cursor: pointer;
        margin: 1.2rem auto;
    }
    .block p{
        font-weight: bold;
    }
</style>