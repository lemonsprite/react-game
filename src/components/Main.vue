<template>
  <div class="main" v-if="tampilkan" @click="stopTimer">Klik Disini!</div>
</template>

<script>
export default {
  name: "MainComp",
  props: ["delay"],
  data() {
    return {
      tampilkan: false,
      timer: null,
      waktuReflek: 0,
      tampilkanHasil: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.tampilkan = true;
      this.mulaiTimer();
    }, this.delay);
  },
  methods: {
    mulaiTimer() {
      this.timer = setInterval(() => {
        this.waktuReflek += 1;
      }, 1);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("selesai", this.waktuReflek);
    },
  },
};
</script>

<style>
.main {
  width: 400px;
  border-radius: 20px;
  background: #0cc798;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
