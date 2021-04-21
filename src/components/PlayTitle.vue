<template>
    <div class="system">
                <button class="prev" @click="prev">Prev</button>
                <button class="play" v-if="!Playing" @click="play">Play</button>
                <button class="pause" v-else  @click="pause">Pause</button>
                <button class="next" @click="next">Next</button>
                
            </div>   
</template>

<script>

export default {
    name:'PlayTitle',

    props:{
        play:Function,
        next:Function,
        prev:Function,
        pause:Function,
        Playing:Boolean

    },
    data() {
        return{
            
        }

    }
    
}
</script>