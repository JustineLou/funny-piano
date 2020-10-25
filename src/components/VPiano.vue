 <template>
<!--Afficher le piano et ses touches du clavier-->

    <div>
        <div class="piano-container" id="note.name">
            <div class="key-white" v-for='note in whiteNotes' :key='note.name' @click="onClick(note)" :keycode="note.keyCode" @keydown="onKeyDown()" @keyup="onKeyUp()" id="note.name"></div>
            <div class="key-black-container">
                <div class="key-black" v-for='note in blackNotes' :key='note.name' @click="onClick(note)"  :keycode="note.keyCode" @keydown="onKeyDown()" @keyup="onKeyUp()" id="note.name"></div> 
            </div>
        </div>

 <!-- Afficher les notes du piano-->
        <div class="notes-container">
            <div class="notes" v-for="note in whiteNotes" :key="note.name"  >
                    <p>{{ note.name }}</p>
            </div>
        </div>
    </div>
     
  
</template>

<script>
export default {
    name: 'VPiano',
    data(){
        return {
            whiteNotes: [
                {
                    name: 'DO',
                    sound: 'C',
                    keyCode: 81
                },                                         
                {                                
                    name: 'RE',
                    sound: 'D',
                    keyCode: 83
                },
                {
                    name: 'MI',
                    sound: 'E',
                    keyCode: 68
                },
                {
                    name: 'FA',
                    sound: 'F',
                    keyCode: 70
                },
                {                                
                    name: 'SOL',
                    sound: 'G',
                    keyCode: 71
                },                               
                {
                    name: 'LA',
                    sound: 'A',
                    keyCode: 72
                },
                {
                    name: 'SI',
                    sound: 'B',
                    keyCode: 74
                },
            ],
            blackNotes: [
                {                               
                    name: 'do#',
                    sound: 'C#',
                    keyCode: 90
                },
                {
                    name: 're#',
                    sound: 'D#',
                    keyCode: 69
                },
                {
                    name: 'fa#',
                    sound: 'F#',
                    keyCode: 84
                },      
                {
                    name: 'sol#',
                    sound: 'G#',
                    keyCode: 89
                },  
                {                                
                    name: 'la#',
                    sound: 'A#',
                    keyCode: 85
                }
            ]
        }   
    },
     mounted(){
        this.audio = document.createElement('audio');
        this.componentEmoji = this.$parent.$children[1];     
        this.addListeners()
    },
    
    methods: {
        //En appuyant sur la souris, le son associée à la note est lancé, un émoji aléatoire apparait
       
        onClick(note) {
            const noteName = encodeURIComponent(note.sound);
            this.audio.src = `/assets/sounds/${noteName}.mp3`;
            this.audio.play();
            this.componentEmoji.generateEmoji(); 
        },

        addListeners() {
            document.addEventListener('keydown', this.onKeyDown)
            document.addEventListener('keyup', this.onKeyUp)
        },

        onKeyDown(e){
            console.log(e.keyCode);
        },

        onKeyUp(){
        }
    }
}
</script>


<style lang="postcss"  scoped>
/*CONSTRUCTION DU PIANO*/
.piano-container{
    position: relative;
    height: 276px;
    width: 531px;
    display: flex;
    justify-content: space-between;
    padding: 10px;
    border-radius: 10px;
    background-color: #000000;
}

/*TOUCHES DU PIANO*/

.key-white{
    position: absolute;
    background: #FFFFFF;
    height: 252px;
    width: 69px;
    top: 4.35%;
    bottom: 4.35%;
}

.key-white:active{
    background: #FFD12D;
}

/*
.key-white:nth-child(1):active ~ .notes-container:nth-child(1){
    opacity: 1;
}*/

.key-black{
    position: absolute;
    background: #000000;
    border-radius: 0px 0px 5px 5px;
    height: 184px;
    width: 30px;    
    top: 4.35%;
    bottom: 28.99%;
}

.key-black:active{
    background: #E6016F;
}

.key-white:nth-child(1){
    border-radius: 5px 0px 0px 5px;    
    left: 2.26%;
}


.key-white:nth-child(2){
    left: 16.01%;
}


.key-white:nth-child(3){
    left: 29.76%;
}

.key-white:nth-child(4){
    left: 43.5%;
}

.key-white:nth-child(5){
    left: 57.25%;
}

.key-white:nth-child(6){
    left: 71%;
}

.key-white:nth-child(7){
    left: 84.75%;
    border-radius: 0px 5px 5px 0px;
}

.key-black:nth-child(1){
    left: 12.81%;
}

.key-black:nth-child(2){
    left: 26.55%;
}

.key-black:nth-child(3){
    left: 54.05%;
  }

.key-black:nth-child(4){
    left: 67.8%;
}

.key-black:nth-child(5){
    left: 81.54%;
}


/*NOTES DU PIANO*/


.notes-container{
    display: flex;
    margin-bottom: 24px;
    height: 22px;
    width: 100%;
    margin-top: 50px;
    color: white;
    opacity: 0.4;
    font-family: "PT Mono", monospace;
    font-size: 20px;
    line-height: 22px;
    justify-content: space-around;
    }

@media only screen and (max-width: 767px) {
    .piano-container {
        max-height: 190px ;
        max-width: 368px ;
    }
    .notes-container {
        display: none;
    }
    
    .key-white{
        max-height: 173px;
        max-width: 48px;
    }

    .key-black{
        max-height: 126px;
        max-width: 21px;
    }
}


</style>