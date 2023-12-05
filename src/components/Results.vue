<template>
    <div>
      <p>Reaction time - {{ score }} ms</p>
      <p class="rank">{{ computedRank }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['score'],
    computed: {
      computedRank() {
        if (this.score < 250) {
          return "Ninja";
        } else if (this.score < 400) {
          return "Rapid Reflexes";
        } else {
          return "Snail pace...";
        }
      },
    },
  };
  </script>
  
  <style>
  .rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
  </style>
  