<template>
  <div :class="[$style.playerIcon, $style[color]]">
    <span :class="[$style.initials]">{{ initials }}</span>
  </div>
</template>

<style module>
  .playerIcon {
    border-radius: 50%;
    width: 2em;
    height: 2em;
    margin-right: 0.5em;
  }

  .red {
    background-color: #ff000030;
    border: 3px solid red;
    color: red;
  }
 .red:hover {
    background-color: #ff000020;
  }
  .blue {
    background-color: #4876e930;
    border: 3px solid #4876e9;
    color: #4876e9;
  }
  .blue:hover {
    background-color: #4876e920;
  }
  .aqua {
    background-color: #0acfdd30;
    border: 3px solid #0acfdd;
    color: #0acfdd;
  }

  .aqua:hover {
    background-color: #0acfdd20;
  }
  .initials {
    font-weight: bold;
    text-align: center;
    line-height: 2em;
    display: flex;
    flex-direction: column;
  }
</style>

<script>
  export default {
    name: 'PlayerIcon',
    props: {
      name: String,
      color: String,
    },
    data() {
      return {
        initials: this.name.charAt(0),
      }
    },
    methods: {}
  }
</script>
