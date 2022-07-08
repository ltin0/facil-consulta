<template>
<div>
    <div class="pg-wrap" v-if="step == 1">
        <div class="progress mt-5 mb-5" style="width: 70%; height: 30px">
            <div
                class="progress-bar"
                v-bind:style="ProgressBar1"
            ></div>
        </div>
        <p>{{page}}</p>
    </div>
    
     <!-- <div class="pg-wrap" v-if:="step == 2">
        <div class="progress mt-5 mb-5" style="width: 70%; height: 30px">
            <div
                class="progress-bar" 
                    v-bind:style="ProgressBar2"
            ></div>
        </div>
        <p>{{page}}</p>
    </div> -->
</div>
</template>

<script>
export default {
    name: 'ProgressBar',
    data(){
        return{
            step: 1,
            totalSteps: 3,
            ProgressBar1: 'width: 50%; height: 30px; background-color: #483698',
            ProgressBar2: 'width: 100%; height: 30px; background-color: #483698',

        }
    },

    props: {
            page : String 

    },


    computed :{
        cssProps(){
            return{
                
                
            }
        }
    }



    };
    

</script>

<style>



</style>
