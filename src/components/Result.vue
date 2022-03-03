<template>
  <p>Score {{ score }} ms</p>
  <p class="rank">Rank {{ rank }}</p>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Fast';
    } else if (this.score < 400) {
      this.rank = 'Medium';
    } else {
      this.rank = 'Be Fast';
    }
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
