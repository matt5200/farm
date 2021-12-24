<template>
  <div class="row">
    <div class="col-md-5">
      <h1 class="m">Schedule Your Visit Today</h1>
      <label for="forVisitDate">Date of visit</label>
      <datepicker v-model="time1" valueType="format" class="pb-3" placeholder="Select Date"></datepicker>
      <div class="form-group pb-3">
        <label for="inputName">Name</label>
        <input
          type="name"
          class="form-control"
          id="inputName"
          aria-describedby="nameHelp"
          placeholder="Enter name"
          required
        />
      </div>
      <div class="form-group pb-3">
        <label for="exampleInputEmail1">Email address</label>
        <input
          type="email"
          class="form-control"
          id="exampleInputEmail1"
          aria-describedby="emailHelp"
          placeholder="Enter email"
        />
      </div>
      <div class="form-group pb-3">
        <div v-if="show">
          <label for="bringingOthers">Scheduling for a group?</label>
          <input
            type="checkbox"
            class="form-check-input"
            id="bringingOthers"
            v-on:click="show = !show"
          />
        </div>
        <div v-else>
          <label for="bringingOthers">Scheduling for a group?</label>
          <input
            type="checkbox"
            class="form-check-input"
            id="bringingOthers"
            v-on:click="show = !show"
          />
          <input
            type="count"
            class="form-control"
            id="inputCount"
            aria-describedby="nameHelo"
            placeholder="Party total"
          />
        </div>
      </div>
      <div>
        <button v-on:click="submitted=true" type="submit" class="btn btn-primary">Submit</button>
      </div>
      <div v-if="submitted">
        <h1> Thank you for your request! We will reach out soon. </h1>
      </div>
    </div>
    <div class="col-md-5">
      <Forecast v-if="weather" :weather="weather" />
    </div>
  </div>
</template>


<script>
import Forecast from "../components/Forecast.vue";
// import Datepicker from "vuejs-datepicker";

import Datepicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';

export default {
  async fetch() {
    this.weather = await fetch(
      "https://api.weather.gov/gridpoints/SEW/125,50/forecast"
    ).then((res) => res.json());
  },
  components: { Datepicker, Forecast },
  data() {
    return {
      value: "",
      context: null,
      show: true,
      weather: undefined,
      submitted: false,
      time1: null
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@import "~/node_modules/bootstrap/scss/bootstrap.scss";
@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";
</style>
