<template>
  <div :class="[$style.container]">

    <h3 :class="[$style.title]">
      <span :class="[$style.icon]" v-if="icon === 'movie'"><MovieIcon /></span>
      <span :class="[$style.icon]" v-else-if="icon === 'music'"><MusicIcon /></span>
      <span :class="[$style.icon]" v-else-if="icon === 'hero'"><HeroIcon /></span>
      <span :class="[$style.icon]" v-else-if="icon === 'drama'"><DramaMasksIcon /></span>
      {{ name }}
    </h3>
    <p>{{ description }}</p>
  </div>
</template>

<style module>
  .container {
    background: rgba(251, 183, 101, 0.585);
    border: 2px solid rgba(251, 183, 101);
    width: 200px;
    height: 150px;
    border-radius: 1em;
    padding: 0.5em 1em;
    float: left;
  }
  .container:hover {
    background: rgba(251, 183, 101, 0.8);
    cursor: pointer;
  }
  .title {
    display: flex;
    align-items: center;
  }
  .icon {
    width: 1.5em;
    height: 1.5em;
    margin-right: 0.25em;
  }
</style>

<script>
import MovieIcon from 'vue-material-design-icons/MovieOpen.vue';
import MusicIcon from 'vue-material-design-icons/Music.vue';
import HeroIcon from 'vue-material-design-icons/Sword.vue';
import DramaMasksIcon from 'vue-material-design-icons/DramaMasks.vue';

  export default {
    name: 'DeckTile',
    props: {
      icon: String,
      name: String,
      description: String,
    },
    components: {
    MovieIcon,
    MusicIcon,
    HeroIcon,
    DramaMasksIcon
},
    data() {
      return {
        initials: this.name.charAt(0),
      }
    },
    methods: {}
  }
</script>
