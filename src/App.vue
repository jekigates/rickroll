<template>
  <div id="app">
    <div>
      <h1 id="teks1"></h1>
      <h1 id="teks2"></h1>
      <h1 id="teks3"></h1>
      <video
        style="display: none"
        width="320"
        height="240"
        controls
        id="video-rickroll"
        poster="@/assets/friendship.jpg"
      >
        <source src="@/assets/rickroll.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function () {
    return {
      kalimat1: "Hi, Nama!",
      kalimat2: "Ini aku, Nama. Aku mau liatin video bermakna.",
      kalimat3: "Tolong dilihat sampai habis ya.",
      i1: 0,
      i2: 0,
      i3: 0,
    };
  },
  mounted: function () {
    this.getNama();
    this.getAsal();
    this.ubahKalimat1();
  },
  methods: {
    getNama() {
      const queryString = window.location.search;
      const urlParams = new URLSearchParams(queryString);
      const nama = urlParams.get("nama");

      if (nama != null) {
        this.kalimat1 = `Hi, ${nama}!`;
      }
    },
    getAsal() {
      const queryString = window.location.search;
      const urlParams = new URLSearchParams(queryString);
      const asal = urlParams.get("asal");

      if (asal != null) {
        this.kalimat2 = `Ini aku, ${asal}. Aku mau liatin video bermakna.`;
      }
    },
    ubahKalimat1() {
      const timer1 = setInterval(() => {
        if (this.i1 < this.kalimat1.length) {
          document.getElementById("teks1").innerHTML += this.kalimat1[this.i1];
          this.i1++;
        } else {
          clearInterval(timer1);
          this.ubahKalimat2();
        }
      }, 100);
    },
    ubahKalimat2() {
      const timer2 = setInterval(() => {
        if (this.i2 < this.kalimat2.length) {
          document.getElementById("teks2").innerHTML += this.kalimat2[this.i2];
          this.i2++;
        } else {
          clearInterval(timer2);
          this.ubahKalimat3();
        }
      }, 100);
    },
    ubahKalimat3() {
      const timer3 = setInterval(() => {
        if (this.i3 < this.kalimat3.length) {
          document.getElementById("teks3").innerHTML += this.kalimat3[this.i3];
          this.i3++;
        } else {
          clearInterval(timer3);
          document.getElementById("video-rickroll").style.display = "inline";
          this.playRickroll();
        }
      }, 100);
    },
    playRickroll() {
      setTimeout(() => {
        document.getElementById("video-rickroll").play();
        // location.href = "https://youtu.be/dQw4w9WgXcQ";
      }, 3000);
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
