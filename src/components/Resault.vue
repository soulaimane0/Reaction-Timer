<template>
    <div class="backResault" @click.self="hide">
        <div class="resault">
            <p>The Reaction Time is : {{ score }}  ms</p>
            <span>{{ rank }}</span>
        </div>
    </div>
</template>

<script>
    export default{
        props:['score'],
        data(){
            return{
                rank:'',
            }
        },
        methods: {
            hide(){
                this.$emit('hideResault')
            }
        },
        mounted(){
            if(this.score < 250) this.rank = 'Ninja Fingers';
            else if(this.score < 400) this.rank = 'Fast';
            else if(this.score < 600) this.rank = 'Intermediate';
            else this.rank = 'Slow';
        }
    }
</script>

<style>
    .backResault{
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.5);
        position: fixed;
        top: 0;
    }
    .resault{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 4.1rem auto;
        width: 400px;
        height: 200px;
        border-radius: 10px;
        background: lightgreen;
        color:rgb(52, 50, 50);
        font-weight: bold;
        font-size: 1.5rem;
        animation: zoom-in-zoom-out 1s ease infinite;
    }
    .resault span{
        color: crimson;
    }
    /* @keyframes zoom-in-zoom-out{
        0%{
            transform: scale(1,1);
        }
        50%{
            transform: scale(1.5,1.5);
        }
        100%{
            transform: scale(1,1);
        }
    } */
</style>