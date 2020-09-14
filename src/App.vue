<template>
  <div id="app">
    <SearchInput />
    <Location />
    <Temperature />
    <Cloud />
    <Sun />
    <Humidity />
    <Wind />
  </div>
</template>

<script>
import SearchInput from './components/SearchInput.vue';
import Location from './components/Location.vue';
import Temperature from './components/Temperature';
import Cloud from './components/Cloud.vue';
import Sun from './components/Sun.vue';
import Humidity from './components/Humidity.vue';
import Wind from './components/Wind.vue';

export default {
  name: 'App',
  components: {
    SearchInput,
    Location,
    Temperature,
    Cloud,
    Sun,
    Humidity,
    Wind

  }
}
</script>

<style>

</style>
