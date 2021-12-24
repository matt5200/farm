<template>
  <div>
    <h1 class="m">Our current forecast</h1>
    <button v-on:click="toggleCelsius" type="submit" class="btn btn-primary">
      Change temperature units (C/F)
    </button>
    <ul>
      <li
        class="forecast"
        v-for="period in weather.properties"
        :key="period.name"
      >
        <b>{{ period.name }}:</b>
        {{getTemp(period.temperature , period.temperatureUnit)}},
        {{ period.shortForecast }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showCelsius: false,
    };
  },
  name: "Forecast",
  // Set component props
  props: {
    weather: {
      type: Object,
      required: true,
    },
  },
  methods: {
    getTemp(temp, tempUnit) {
      if (this.showCelsius) {
        return Math.floor((((Number(temp) - 32) * 5) / 9)) + "C";
      } else {
        return temp + tempUnit;
      }
    },
    toggleCelsius() {
      this.showCelsius = !this.showCelsius;
    },
  },
};
</script>


<style lang="scss">
// Store page content

.forecast {
  display: block;
}

@import "~/node_modules/bootstrap/scss/bootstrap.scss";
@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";
</style>
