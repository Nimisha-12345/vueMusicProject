<template>
    <section class="playlist">
            <h3>Playlist</h3>
            <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' : 'song'">
                {{song.title}} -  {{song.artist}}
            </button>
        </section>
</template>


<script>
export default {
    name:'PlayTrack',
    props:{
        songs:Array,
        current:Object,
        play:Function

        
        
    }
}
</script>