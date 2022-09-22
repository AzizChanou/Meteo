<template>
  <img
    src="../assets/Clear.png"
    alt="Icon"
    class="animate-pulse"
    v-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/Cloud-background.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/Hail.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/HeavyCloud.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/HeavyRain.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/LightCloud.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/LightRain.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'ok'"
  />
  <img
    src="../assets/Shower.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'it'"
  />
  <img
    src="../assets/Sleet.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/Snow.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img
    src="../assets/Thunderstorm.png"
    alt="Icon"
    class="animate-pulse"
    v-else-if="icon == 'Clear Sky'"
  />
  <img src="../assets/Clear.png" alt="Icon" class="animate-pulse" v-else />
</template>

<script setup>
defineProps({ icon: "" });
</script>
