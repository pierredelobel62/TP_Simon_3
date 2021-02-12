<template>
  <div id="home">
    <PlayButton v-on:launch-game="launchCountdown"></PlayButton>
    <Level ref="levelComponent" v-show="gameLaunched"></Level>
    <Countdown
      v-show="gameLaunched"
      ref="countdownComponent"
      v-on:finish="launchGame"
    ></Countdown>
    <div id="buttons" v-show="gameLaunched">
      <SimonButton
        v-for="button in buttons"
        v-bind:key="button.name"
        v-bind:data="button"
        v-on:click="clickButton"
      >
      </SimonButton>
    </div>
  </div>
</template>

<script>
import SimonButton from "./SimonButton.vue";
import Countdown from "./Countdown.vue";
import PlayButton from "./PlayButton.vue";
import Level from "./Level.vue";

export default {
  name: "Home",
  components: {
    SimonButton,
    Countdown,
    PlayButton,
    Level
  },
  data() {
    return {
      gameLaunched: false,
      countdown: null,
      buttons: [
        { name: "red", active: false, sound: new Audio(require('@/assets/sounds/red.ogg')) },
        { name: "yellow", active: false, sound: new Audio(require('@/assets/sounds/yellow.ogg'))},
        { name: "purple", active: false, sound: new Audio(require('@/assets/sounds/green.ogg')) },
        { name: "blue", active: false, sound: new Audio(require('@/assets/sounds/blue.ogg')) },
      ],
      combinaisonJeu: [],
      combinaisonJoueur: [],
    };
  },
  methods: {
    launchCountdown: function () {
      this.gameLaunched = true;
      this.$refs.countdownComponent.launch();
    },
    launchGame: function () {
      this.getRandomColor();
    },
    clickButton: function (button) {
      this.combinaisonJoueur.push(button);
      this.checkPattern();
    },
    playButton: function (button) {
      button.active = true;
      button.sound.play();
      setTimeout(() => {
        button.active = false;
      }, 500);
    },
    getRandomColor: function () {
      const that = this;
      const rand = Math.floor(Math.random() * 4);
      that.combinaisonJeu.push(that.buttons[rand]);

      that.combinaisonJeu.forEach((button, index) => {
        setTimeout(() => {
          this.playButton(button);
        }, 1000 * (index + 1));
      });
    },
    checkPattern: function () {
      let right = true;
      this.combinaisonJoueur.forEach((key, value) => {
        if (key != this.combinaisonJeu[value]) {
          right = false;
        }
      });

      if (!right) {
        alert("Vous avez perdu ! Retour au niveau 1");
        this.$refs.levelComponent.restartLevel();
        this.combinaisonJeu = [];
        this.getNextMove();
      } else if (this.combinaisonJeu.length === this.combinaisonJoueur.length) {
        this.$refs.levelComponent.levelUp();
        this.getNextMove();
      }

    },
    getNextMove: function() {
      this.combinaisonJoueur = [];
        setTimeout(() => {
        this.getRandomColor();
      }, 2000);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
#home {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
