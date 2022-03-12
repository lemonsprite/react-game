<template>
  <h1>Seberapa Cepet Reflek Lu!</h1>

  <button @click="start" :disabled="mulai">
    <box-icon name="play" color="#fff" />
    <p>Mulai</p>
  </button>
  <Main v-if="mulai" :delay="delay" @selesai="gameSelesai" />
  <Hasil v-if="tampilkanHasil" :score="hasilScore" />
</template>

<script>
import Main from "./components/Main.vue";
import Hasil from "./components/Hasil.vue";

export default {
  name: "App",
  components: {
    Main,
    Hasil,
  },
  data() {
    return {
      mulai: false,
      delay: null,
      hasilScore: null,
      tampilkanHasil: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 8000;
      this.mulai = true;
      this.tampilkanHasil = false;
    },
    gameSelesai(e) {
      this.hasilScore = e;
      this.mulai = false;
      this.tampilkanHasil = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: auto;
  background: #0faf87;
  border-radius: 5px;
  padding: 0.2rem 0.8rem;
  color: white;
  border: none;
  outline: none;
  cursor: pointer;
}
button[disabled] {
  opacity: 0.2;
}
button p {
  margin-left: 0.2rem;
}
</style>
