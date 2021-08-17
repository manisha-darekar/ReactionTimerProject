<template>
<div class="block" v-if="showblock" @click="stoptimer">Click Me</div>
  
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            showblock:false,
            timer:null,
            reactiontimer:0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showblock=true
            this.starttimer()
            
        }, this.delay);
    },
    methods:{
        starttimer()
        {
            this.timer=setInterval(() => {

                this.reactiontimer+=10
                
            }, 10);


        },
        stoptimer(){

                clearInterval(this.starttimer)
                this.$emit('end',this.reactiontimer)


        }
    }


}
</script>

<style>
.block{

    width: 400px;
    border-radius: 10px;
    text-align: center;
    background: rgb(64, 209, 209);
    color: white;
    padding: 100px 0;
    margin: 40px auto;
}

</style>