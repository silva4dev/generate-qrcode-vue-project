<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <div>
      <input
        type="text"
        size="25"
        placeholder="Digite para gerar..."
        v-model="text"
      />
    </div>

    <div v-if="text" class="output">
      <img :src="newQRCode" alt="QRCode" />
    </div>
  </div>
</template>

<script>
import QRious from "qrious";
export default {
  name: "App",
  data() {
    return {
      title: "Gerador QRCode",
      text: "https://www.google.com.br",
      qrcode: new QRious({ size: 300 }),
    };
  },
  computed: {
    newQRCode() {
      this.qrcode.value = this.text;
      return this.qrcode.toDataURL();
    },
  },
};
</script>

<style>
@font-face {
  font-family: "RobotoMono";
  src: url("./assets/fonts/RobotoMono-Thin.ttf");
}

* {
  font-family: "RobotoMono", monospace;
}

body {
  display: flex;
  justify-content: center;
  text-align: center;
  color: #fff;
  background: linear-gradient(to right, rgb(19, 106, 138), rgb(38, 120, 113));
}

input {
  font-size: 2em;
  margin-bottom: 30px;
}

.output {
  border: 1px solid #222;
  padding: 30px 15px;
  background-color: #0006;
}
</style>
