<template>
  <div class="app" id="app">
    <h1>{{ title }}</h1>
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


export default {
  name: 'App',
  components: {
    PlayerIcon,
    DeckTile
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
  width: 960px;
  margin: 0 auto;
}

.main {
  display: flex;
  flex-direction: column;
}

.divider {
  border-top: 1px solid rgba(251, 183, 101);
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
