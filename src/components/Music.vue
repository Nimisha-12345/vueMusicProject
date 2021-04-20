<template>
    <div class="container" >
        <section class="player">
            <h2 class="song_title">{{current.title}}</h2>
                <span>{{current.artist}}</span>
            
            <div class="system">
                <button class="prev" @click="prev">Prev</button>
                <button class="play" v-if="!Playing" @click="play">Play</button>
                <button class="pause" v-else @click="pause">Pause</button>
                <button class="next" @click="next">Next</button>
            </div>                 
        </section>
        <section class="playlist">
            <h3>Playlist</h3>
            <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' : 'song'">
                {{song.title}} -  {{song.artist}}
            </button>
        </section>
    </div>
</template>

<script>
export default {
    data() {
        return {
            current: {},
            index: 0,
            Playing:false,
            
            songs:[
                {
                    title:'lamb',
                    artist:'arjit',
                    src: require('../assets/nimi-1.mp3'),
                
                    
                },
                {
                   title:'ariana',
                   artist:'ariana granda',
                   src: require('../assets/nimi-2.mp3'),
                   
                   
                },
                {
                    title:'often',
                    artist:'post man',
                    src: require('../assets/nimi-3.mp3'),
                    //image: require('../assets/nimi-3.jpg')
        
                    
                    
                }

            ],
            player: new Audio()
        }
    },
    methods:{
        play(song){
            if(typeof song.src != "undefined"){
                this.current = song;

                this.player.src = this.current.src;
            }
            this.player.play();
            this.player.addEventListener('ended', function(){
                this.index++;
                if(this.index > this.songs.length - 1){
                    this.index = 0;
                }
                this.current = this.songs[this.index];
                this.play(this.current);
            }. bind(this));
            this.Playing = true;
        },
        pause(){
            this.player.pause();
            this.Playing = false;
        },
        next(){
            this.index++;
            if(this.index > this.songs.length - 1){
                this.index = 0;
            }
            this.current = this.songs[this.index];
            this.play(this.current);
        },
        prev(){
             this.index--;
            if(this.index < 0){
                this.index = this.songs.length - 1;
            }
            this.current = this.songs[this.index];
            this.play(this.current);

        }

    },
    created() {
        this.current = this.songs[this.index];
        this.player.src = this.current.src;
    }
}
</script>
