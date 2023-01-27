<template>
  <div class="app" id="app">
    <div class="nav">
    <h1 class="title">
      <span class="logo"><AirBalloonIcon size="44" fillColor="rgb(255 153 31)" /></span>
      <span class="titleText">
        <span class="w">W</span>
        <span class="ordsup">ordsUp</span>
      </span>
    </h1>

    </div>
    <div class="main">
      <div class="decks">
        <h2>Decks</h2>
          <div class="deckTiles">
            <DeckTile
              v-for="deck in decks"
              v-bind:key="deck.name"
              :name="deck.name"
              :description="deck.description"
              :icon="deck.icon"
            ></DeckTile>
          </div>
      </div>
      <div class="divider" />
      <div class="players">
        <h2>Players</h2>
        <div class="playerIcons">
          <PlayerIcon color="red" name="Kelly"/>
          <PlayerIcon color="blue" name="Jon"/>
          <PlayerIcon color="aqua" name="Freya"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PlayerIcon from './components/PlayerIcon.vue';
import DeckTile from './components/DeckTile.vue';
import data from './data/decks.json';
import AirBalloonIcon from 'vue-material-design-icons/Bee.vue';

export default {
  name: 'App',
  components: {
    PlayerIcon,
    DeckTile,
    AirBalloonIcon
  },
  data() {
    return {
      error: false,
      name: '',
      title: "WordsUp",
      decks: [],
      details: { Name: "Bill Murray", Age: 72, Location: "Chicago "}
    }
  },
  methods: {
    updateCart() {
      this.cart++;
      this.tickets--;
    },
  },
  computed: {
    soldOut() {
      return this.tickets === 0;
    }
  },
  mounted() {
    this.decks = data;
  }
}
</script>

<style>
body {
  color: #222;
  font-family: Arial, Helvetica, sans-serif;
  margin: 0;
  padding: 0;
}

ul {
  padding-left: 2em;
}

button, input {
  line-height: 1.5em;
  padding: 0.25em .5em;
  background: white;
  border-radius: 3px;
  border-color: #ddd;
  border-width: 1px;
  border-style: solid;
}

.app {
  background: #ffce74;
}

.title {
  margin: 0;
  padding: .25em;
  width: 960px;
  margin: 0 auto;
  line-height: 36px;
  margin-top: 0.4em;
}

.titleText {
  font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  margin-left: 27px;
  position: relative;
}

.w {
  rotate: 21deg;
  position: absolute;
  top: -5px;
  left: 7px;
}

.ordsup {
  margin-left: 40px;
  position: absolute;
}

.logo {
  position: absolute;
  top: -4px;
}
.nav {
  background-color: white;
  border-bottom: 2px solid rgb(255 153 31);
  padding: 0.25em;
}

.main {
  display: flex;
  flex-direction: column;
  width: 960px;
  margin: 0 auto;
  background:white;
  padding: 1em 3em;
}

.divider {
  margin-top: 3em;
  border-top: 1px solid rgb(255 153 31);
}

.deckTiles {
  display: grid;
  grid-template-columns: repeat(4, 1fr);

  /* grid-template-columns:  repeat(auto-fill, minmax(200px, 250px)); */
  grid-column-gap: 10px;
  grid-row-gap: 10px;
}

.players {
  display: flex;
  flex-direction: column;
  gap: 1em;
}

.playerIcons {
  display: flex;
}

</style>
