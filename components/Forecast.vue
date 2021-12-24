<template>
  <div>
    <h1 class="m">Our current forecast</h1>
    <ul>
      <li
        class="forecast"
        v-for="period in weather.properties.periods"
        :key="period.name"
      >
        <b>{{ period.name }}:</b>
        {{ period.temperature }}{{ period.temperatureUnit }},
        {{ period.shortForecast }}
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: "Forecast",
  // Set component props
  props: {
    weather: {
      type: Object,
      required: true,
    },
  },
};
</script>


<style lang="scss">
// Store page content

.forecast {
  display: block
}

@import "~/node_modules/bootstrap/scss/bootstrap.scss";
@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";
</style>
