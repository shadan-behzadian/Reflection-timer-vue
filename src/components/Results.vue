<template>
  <p>Your reaction time:{{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return { rank: null };
  },
  mounted() {
    if (this.score <= 250) {
      this.rank = "You Rock";
    } else if (this.score > 250 && this.score < 1000) {
      this.rank = "Rapid reflexes!";
    } else {
      this.rank = "Snail pace ...";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.5rem;
  background: rgb(170, 146, 169);
  width: fit-content;
  margin: auto;
  font-weight: bold;
}
</style>
