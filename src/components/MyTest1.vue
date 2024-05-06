<template >
  <div class="timer" v-if="timerCount">время пошло:{{ timerCount }}</div>
  <div class="timeaut" v-else  > ВРЕМЯ ВЫШЛО</div>

<button class="btnTimer" v-if="restartLevel" @click="shuffleCards">начать сначала</button>
<div class="cards">
  <div class="card-inner " v-for="(card, index) in cards" :key="index" @click="timerCount ?  revealCard(index): null">
    <img  v-if="card.revealed" :src="card.image" alt="Card" class="img card-front" />
    <div v-else class="card-back"></div>
  </div>
</div>

</template>

<script>
export default {
  data() {
    return {
      cards: [
      { image: 'appel.jpg', revealed:false, matched: false },
  { image: 'appel.jpg', revealed: false, matched: false},
  { image: 'grusha.jpg', revealed: false, matched: false },
  { image: 'grusha.jpg', revealed: false, matched: false },
  { image: 'kiwi.jpg', revealed: false, matched: false },
  { image: 'kiwi.jpg', revealed: false, matched: false },
  { image: 'orange.jpg', revealed: false, matched: false },
  { image: 'orange.jpg', revealed: false, matched: false },
  { image: 'strowberri.jpg', revealed: false, matched: false },
  { image: 'strowberri.jpg', revealed: false, matched: false },
  { image: 'banan.jpg', revealed: false, matched: false },
  { image: 'banan.jpg', revealed: false, matched: false },

      ],
      previousCardIndex: null,
      countCard: 0,
      timerCount: 40,

    };
  },
  watch:{
    timerCount: {
      handler(value) {
        if (value>0){
          setTimeout(()=>{
            this.timerCount--;
          },1000
          );
        }
      },
      immediate: true,
    }
  },
  computed: {
    restartLevel: function () {
  const getCards = this.cards.filter(function (card) {
    return !card.matched 
  })
  if(getCards.length === 0 || this.timerCount===0) {
    return true
  }
  return false
    },
    
  },
  methods: {
    revealCard(index) {
      const audio = new Audio('./klik-myishki.mp3')

      audio.play()

      if(this.countCard >=2) {
        return;
      }
      this.countCard++ 
      console.log(this.countCard)


      this.cards[index].revealed = true;
      if (this.countCard === 1) {
        this.previousCardIndex = index
      }
      if (this.countCard === 2) {
        const getCards = this.cards.filter(function (card) {
    
          return card.revealed && !card.matched

        })

        console.log(getCards)
        if (getCards[0].image !== getCards[1].image) {

        setTimeout( function () {
          console.log(this.cards)
          this.cards.forEach(function (card) {
            if ( card.matched === false)
            card.revealed = false
          })   
            }.bind(this), 1000)

        } 
        else {
          this.cards[index].matched = true
          this.cards[this.previousCardIndex].matched = true

        }
        this.countCard = 0;
        this.previousCardIndex = null
      }

    },

    shuffleCards() {
      this.cards.forEach(function(card){
        card.revealed = false
        card.matched = false
      })

      for (let i = this.cards.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [this.cards[i], this.cards[j]] = [this.cards[j], this.cards[i]];
      }

      this.timerCount=40;
              this.countCard = 0;
        this.previousCardIndex = null

    },     

  },
};
</script>


<style>
  .card-back {
    position: relative;
    background:url(@/assets/becCard.jpg);
    background-size: cover;
    width: 200px;
    height: 200px;
    border-radius:20px;
    margin: 10px;
    border: 1px solid #0e0d0d;
  border-radius: 20px;
  box-shadow: 2px 4px 10px 0 rgba(0, 0, 0, 2);
}
  
  .cards {
    padding-left: 200px;
    width: 70%;
    height: auto;
    display: flex;
    flex-wrap: wrap;
  }
  .img {
    width: 200px;
    height: 200px;
    border-radius: 20px;
    margin: 10px;

  }

  .timeaut {
    margin-right: 100px;
    /* margin-bottom: 50px; */
    color:#eb7511;
    font-size: 40px;
    font-weight: bold;
  }

  .timer {
    margin-right: 100px;
    margin-bottom: 20px;
    color: #a8cfa8;
    font-size: 30px;
    font-weight: bold;
  }

  .btnTimer {
    margin-right: 100px;
    margin-bottom: 20px;
    width: 200px;
    height: 60px;
    background:#854611;
    border-radius: 16px;
    font-weight: bold;
    color: #df992f;
    font-size: 15px;
  }

  body {
    background: url(@/assets/backBody2.jpeg) ;
            background-size: cover;

  }

  .card-inner {
    margin: 10px;
  width: 200px;
  height: 200px;
}

.card-inner img {
  max-width: 100%;
  max-height: 100%;
  object-fit: cover;
}

.card-inner .card-back {
  background-color: #ccc;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;

  transition: transform 0.3s;
}
.card-inner:active .card-back {
  transform: rotateY(180deg);
}

.card-front {
  transform: rotateY(180deg);
}
</style>
