<template>
  <div class="w-full h-full p-5">
    <div class="border-2 h-full w-full rounded-lg flex flex-col border-dashed">
      <div class="h-full w-full p-5 flex justify-around items-center">
        <div
          class="p-5 w-72 h-72 bg-gray-50 rounded-lg flex flex-col items-center border-4 border-dashed border-gray-500 pb-12"
        >
          <svg
            class="h-48 text-gray-500"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="0.5"
              d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"
            ></path>
          </svg>
          <p class="text-2xl font-light text-gray-600">
            Light Status :
            <span
              class="font-medium"
              :class="light === 1 ? 'text-green-400' : 'text-red-400'"
              >{{ light === 1 ? "On" : "Off" }}</span
            >
          </p>
        </div>
        <div
          class="p-5 flex-grow ml-7 h-72 bg-gray-50 rounded-lg flex flex-col justify-start items-center pt-10 border-4 border-dashed border-gray-500 pb-12 space-y-5"
        >
          <p class="text-2xl text-gray-600 font-medium underline">
            Group Members
          </p>
          <p class="text-2xl font-light text-gray-600">Wongsakorn 6230613016</p>
          <p class="text-2xl font-light text-gray-600">Warun S. 6230613019</p>
          <p class="text-2xl font-light text-gray-600">Rawich 6230613036</p>
        </div>
      </div>
      <div class="w-full">
        <p class="ml-5 text-gray-600">Temp & Humid Graph</p>
        <apexchart
          type="area"
          height="320"
          :options="chartOptions"
          :series="series"
        ></apexchart>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  props: ["light"],
  data: function() {
    return {
      series: [
        {
          name: "Humid",
          data: [20, 11, 65, 71, 89, 22, 79, 81, 28],
        },
        {
          name: "Temp",
          data: [25, 20, 26, 24, 28, 24, 26, 24, 22],
        },
      ],
      chartOptions: {
        chart: {
          height: 350,
          type: "line",
          toolbar: {
            show: false,
          },
        },
        legend: {
          show: false,
        },
        dataLabels: {
          enabled: false,
        },
        stroke: {
          curve: "smooth",
        },
        xaxis: {
          categories: [
            "5 AM",
            "6 AM",
            "7 AM",
            "8 AM",
            "9 AM",
            "10 AM",
            "11 Am",
            "12 PM",
            "1 PM",
          ],
        },
      },
    };
  },
};
</script>
