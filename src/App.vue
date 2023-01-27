<template>
  <div class="app" id="app">
    <h1>{{ title }}</h1>
    <div class="main">
      <MenuIcon />
      <div class="decks">
        <h2>Decks</h2>
        <ul>
          <li v-for="deck in decks" :key="deck.id">
            <p>{{ deck.name }}</p>
            <p>{{ deck.description }}</p>
            <span v-if="deck.icon === 'movie'"><MovieIcon /></span>
            <span v-else-if="deck.icon === 'music'"><MusicIcon /></span>
            <span v-else-if="deck.icon === 'hero'"><HeroIcon /></span>
          </li>
        </ul>
      </div>
      <div class="players">
        <p>Players</p>
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
import PlayerIcon from './components/PlayerIcon.vue'
import data from './data/decks.json';
import MovieIcon from 'vue-material-design-icons/MovieOpen.vue';
import MusicIcon from 'vue-material-design-icons/Music.vue';
import HeroIcon from 'vue-material-design-icons/Sword.vue';


export default {
  name: 'App',
  components: {
    PlayerIcon,
    MovieIcon,
    MusicIcon,
    HeroIcon
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
  padding: 0 1em;
}

/* .main {
  display: flex;
  gap: 2em;
} */

.players {
  display: flex;
  flex-direction: column;
  gap: 1em;
}

.playerIcons {
  display: flex;
}

</style>
