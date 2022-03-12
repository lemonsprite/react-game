<template>
  <p>Reaksi kamu : {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "HasilComp",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 50) {
      this.rank = "Buset serius bukan Robot!!?";
    } else if (this.score < 100) {
      this.rank = "Mantap, Nice Flick";
    } else if (this.score < 200) {
      this.rank = "Oke standar lah..";
    } else if (this.score < 300) {
      this.rank = "Oalah, Konsen lah!";
    } else if (this.score >= 300 && this.rank <= 500) {
      this.rank = "Serius!!? Mending main pou dah.. ";
    } else if (this.rank > 500) {
      this.rank = "Lag kali otakmu dek!";
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
