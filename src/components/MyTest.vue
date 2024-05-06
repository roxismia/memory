<template>
    <div>
        <input type="range" min="0" max="100" v-model="volume" @input="changeVolume">
        <button @click="togglePlay">{{ isPlaying ? 'Пауза' : 'Воспроизвести' }}</button>
    </div>
</template>
    
<script>
export default {
    data() {
        return {
            audio: new Audio('./fon.mp3'),
            volume: 100,
            isPlaying: false,
        };
    },
    methods: {
        togglePlay() {
            if (this.isPlaying) {
                this.audio.pause();
            } else {
                this.audio.play();
            }
            this.isPlaying = !this.isPlaying;
        },
        changeVolume() {
            this.audio.volume = this.volume / 100;
        },
    },
    created() {
        this.audio.loop = true;
        this.audio.volume = this.volume / 100;
    },
};
</script>
        