<template>
    <div class="container" >
        <section class="player">
            <h2 class="song_title">{{current.title}}</h2>
                <p>{{current.artist}}</p>
            <PlayTitle :play="play" :pause="pause" :next="next" :prev="prev" :Playing="Playing" />
                   
        </section>
        <PlayTrack :songs="songs" :current="current" :play="play" /> 
        
    </div>
</template>

<script>
import PlayTitle from '../components/PlayTitle'
import PlayTrack from  '../components/PlayTrack'
export default {
    name:'Music',
    components:{
        PlayTitle,
        PlayTrack,
    },
    data() {
        return {
            current: {},
            index: 0,
            Playing: false,
            
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
