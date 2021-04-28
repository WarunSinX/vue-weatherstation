<template>
  <div>
    <p class="text-yellow-500 text-xl">TEMP : {{ temp }}</p>
    <p class="text-yellow-500 text-xl">HUMID : {{ humid }}</p>
    <p class="text-yellow-500 text-xl">LIGHT : {{ light }}</p>
    <p class="text-yellow-500 text-xl">RAIN : {{ rain }}</p>
  </div>
</template>

<script>
import io from "socket.io-client";

export default {
  name: "Home",
  data() {
    return {
      socket: {},
      temp: 0,
      humid: 0,
      light: 0,
      rain: 0,
    };
  },
  created() {
    this.socket = io("https://wwp-iot-server.herokuapp.com");
  },
  mounted() {
    this.socket.on("temp", (data) => {
      this.temp = data;
    });
    this.socket.on("humid", (data) => {
      this.humid = data;
    });
    this.socket.on("light", (data) => {
      this.light = data;
    });
    this.socket.on("rain", (data) => {
      this.rain = data;
    });
  },
};
</script>
