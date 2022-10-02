<template>
  <div class="h-screen w-screen max-w-screen fixed bg-primary flex items-center justify-center text-white">
    <div v-if="weatherData.wind" class="w-4/5 h-4/5 space-y-6">
      <div class="w-full flex flex-row space-x-6 justify-between">
        <input type="text" id="city" class="w-4/6 rounded p-3 bg-secondary" @keydown.enter="getWeather()"
          placeholder="Nom de ville ou pays" />
        <button type="submit" @click="getWeather()"
          class="w-2/6 p-3 bg-blue-700 hover:bg-blue-900 duration-300 font-semibold rounded">
          Rechercher
        </button>
      </div>
      <div
        class="w-full flex flex-row justify-between overflow-x-scroll space-x-4 md:space-x-0">
        <div class="bg-secondary p-3 font-bold rounded flex flex-col items-center">
          <span class="uppercase text-xl">Vent</span>
          <div class="text-xl lg:text-3xl my-6">
            <span class="text-3xl lg:text-5xl">{{
            weatherData.wind.speed
            }}</span>mph
          </div>
        </div>
        <div class="bg-secondary p-3 font-bold rounded flex flex-col items-center">
          <span class="uppercase text-xl">Humidité</span>
          <div class="text-xl lg:text-3xl my-6">
            <span class="text-3xl lg:text-5xl">{{
            weatherData.main.humidity
            }}</span>%
          </div>
        </div>
        <div class="bg-secondary p-3 font-bold rounded flex flex-col items-center">
          <span class="uppercase text-xl">Pression</span>
          <div class="text-xl lg:text-3xl my-6">
            <span class="text-3xl lg:text-5xl">{{
            weatherData.main.pressure
            }}</span>hPa
          </div>
        </div>
        <div class="bg-secondary p-3 font-bold rounded flex flex-col items-center">
          <span class="uppercase text-xl">Visibilité</span>
          <div class="text-xl lg:text-3xl my-6">
            <span class="text-3xl lg:text-5xl">{{
            weatherData.visibility
            }}</span>m
          </div>
        </div>
        <div class="bg-secondary p-3 font-bold rounded flex flex-col items-center">
          <span class="uppercase text-xl">Code pays</span>
          <div class="text-xl lg:text-3xl my-6">
            <span class="text-3xl lg:text-5xl">{{
            weatherData.sys.country
            }}</span>
          </div>
        </div>
      </div>
      <div class="w-full h-3/5 rounded bg-secondary p-2 flex flex-col justify-between">
        <div class="flex h-1/6 justify-between font-semibold text-xl">
          <div class="flex flex-col items-center">
            <span class="hidden md:flex">Température</span>
            <span>{{ weatherData.main.temp }} °C</span>
          </div>
          <div class="flex flex-col items-center">
            <span class="hidden md:flex">Température maximale</span>
            <span>{{ weatherData.main.temp_max }} °C</span>
          </div>
        </div>
        <div class="flex flex-col h-4/6 justify-center items-center">
          <img :src="
            'https://openweathermap.org/img/wn/' +
            weatherData.weather[0].icon +
            '@4x.png'
          " class="animate-pulse" alt="" />
          <span class="font-medium text-2xl md:text-3xl uppercase">{{
          weatherData.name
          }}</span>
        </div>
        <div class="flex h-1/6 justify-between font-semibold text-xl">
          <span>{{ weatherData.weather[0].main }}</span>
          <span class="capitalize">{{
          weatherData.weather[0].description
          }}</span>
        </div>
      </div>
    </div>
    <div v-else>
      <div class="w-full flex flex-row space-x-6 justify-between">
        <input type="text" id="city" class="w-4/6 rounded p-3 bg-secondary" @keydown.enter="getWeather()"
          placeholder="Nom de ville ou pays" />
        <button type="submit" @click="getWeather()"
          class="w-2/6 p-3 bg-blue-700 hover:bg-blue-900 duration-300 font-semibold rounded">
          Rechercher
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      key: "0be9f7ea34a151b04c340e2114da5c26",
      weatherData: {},
      city: "Cotonou",
      error: {},
    };
  },
  created() {
    fetch(
      "https://api.openweathermap.org/data/2.5/weather?q=Cotonou&appid=0be9f7ea34a151b04c340e2114da5c26&units=metric&lang=fr"
    )
      .then((res) => res.json())
      .then((data) => (this.weatherData = data))
      .catch((err) => console.log("Erreur " + err.message));
  },
  methods: {
    getWeather() {
      this.city = document.getElementById("city").value;
      fetch(
        "https://api.openweathermap.org/data/2.5/weather?q=" +
        this.city +
        "&appid=" +
        this.key +
        "&units=metric&lang=fr"
      )
        .then((res) => res.json())
        .then((data) => (this.weatherData = data))
        .catch((err) => (this.error = err.message))
    },
  },
};
</script>

<style>
::-webkit-scrollbar {
  width: 0rem;
}

* {
  border-width: 0px;
}
</style>
