<template>
  <div class="container">
    <div class="row">
      <!-- Image with text -->
      <div class="padding row">
        <!-- Set image to user values. A border is applied / removed when image is clicked -->
        <img
          v-bind:src="resolve_img_url(source)"
          v-bind:alt="desc"
          v-bind:title="title"
          v-bind:class="{ 'border border-5': bool }"
          v-on:click="toggle(this.bool)"
        />
        <div class="row box-1 bg-light">
          <p class="font-italic">
            {{ message }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
let bool = true;

// Toggle boolean
const mixin = {
  methods: {
    toggle(bool) {
      this.bool = !this.bool;
      return bool;
    },
  },
};

// Store page content
export default {
  name: "ImageTemplate",
  data() {
    return {
      bool,
    };
  },
  // Set component props
  props: {
    // Image source is required
    source: {
      type: String,
      required: true,
    },
    message: String,
    title: String,
    desc: String,
  },
  methods: {
    // Function to find images
    resolve_img_url: function (path) {
      let images = require.context("../static/", false, /\.png$|\.jpg$/);
      return images("./" + path);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.padding {
  padding: 0px;
}

@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";
</style>
