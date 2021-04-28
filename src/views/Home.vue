<template>
  <div class="sm:h-screen w-full bg-blue-50">
    <div class="h-full w-full flex">
      <div
        :style="{ width: '50rem' }"
        class="h-full bg-gradient-to-r from-blue-200 to-blue-300 flex flex-col items-center py-10"
      >
        <p class="text-2xl text-gray-50 font-bold">
          Weathering With PSU
        </p>
        <div class="mt-2.5 flex">
          <p class="text-xl text-gray-50 mb-3 flex justify-center items-center">
            <locIcon class="h-7 mr-2" />
            PSU Phuket Station
          </p>
        </div>
        <div class="mt-10">
          <p class="text-2xl font-light text-gray-50 text-right mb-3">
            <span>tempreture</span>
          </p>
          <p class="text-9xl font-light text-gray-50 animate-pulse">
            24°c
          </p>
        </div>
        <div class="mt-10">
          <p class="text-2xl font-light text-gray-50">
            humid : <span class="animate-pulse">100%</span> | Raining :
            <span class="animate-pulse">Yes</span>
          </p>
        </div>
        <div
          class="mt-16 w-44 h-44 bg-white rounded-lg p-2 cursor-pointer shadow-sm"
          @click="clickLine"
        >
          <img src="../assets/lineCode.png" class="opacity-70" />
        </div>
      </div>
      <div class="h-full w-full bg-gray-50 hidden sm:block">
        <dashboard />
      </div>
    </div>
  </div>
</template>

<script>
import io from "socket.io-client";
import locIcon from "../components/locIcon";
import Dashboard from "../components/Dashboard.vue";

export default {
  name: "Home",
  components: { locIcon, Dashboard },
  data() {
    return {
      socket: {},
      temp: 0,
      humid: 0,
      light: 0,
      rain: 0,
    };
  },
  methods: {
    clickLine: function() {
      window.open(
        "https://liff.line.me/1645278921-kWRPP32q?accountId=273wnizr&openerPlatform=native&openerKey=talkroom%3Aheader#mst_challenge=29Lgv7AecXtMm6yKDEBoyJIxhroACK8QdohwcqnErJs",
        "_blank"
      );
    },
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

<style>
@import url("https://fonts.googleapis.com/css2?family=Ubuntu:wght@300;400;700&display=swap");
* {
  font-family: "Ubuntu", sans-serif;
}
</style>
