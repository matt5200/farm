<template>
  <div class="main" id="app">
    <div class="container">
      <!-- Header -->
      <div class="row header">
          <div class="col">
          <i class="fa fa-tractor"></i>
          </div>
          Blissful Farms
          <div class="col text-end">
              <i class="fa fa-tractor"></i>
          </div>
      </div>
      <!-- Navbar with routes to other pages -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="navbar">
          <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
              <li class="nav-item">
                <nuxt-link class="nav-link" to="/">Home</nuxt-link>
              </li>
                <li class="nav-item">
              <nuxt-link class="nav-link" to="/Blog">Blog</nuxt-link>
              </li>
              <li class="nav-item">
                <nuxt-link class="nav-link" to="/Testimonials">Testimonials</nuxt-link>
              </li>
              <li class="nav-item">
                <nuxt-link class="nav-link" to="/About">About</nuxt-link>
              </li>
              <li class="nav-item">
                <nuxt-link class="nav-link" to="/Api">Schedule</nuxt-link>
              </li>
            </ul>
          </div>
      </nav>
    <router-view/>
    <Foot/>
  </div>
</div>
</template>


<script>


</script>

<style lang="scss">
// Store page content

@import '~/node_modules/bootstrap/scss/bootstrap.scss';
@import "../scss/_base.normalize.scss";
@import "../scss/_components.content.scss";
@import "../scss/_settings.responsive.scss";
@import "../scss/_settings.variables.scss";
@import "../scss/style.scss";


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

// Format nav bar
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

// Format tractor icon
.fa-tractor {
  display: inline-block;
  font-size: 40px;
}

// Format header
.header {
  display: flex;
  font-family: 'Roboto Condensed', sans-serif;
  font-size: 60px;
  justify-content: center;
  align-items: center;
  @include media-query("infograph") {
    font-size: 25px;
    .fa-tractor {
      display: inline-block;
      font-size: 20px;
    }
  }
}

.box-1 {
  border-radius: 20px;
}

.box-2 {
  border-radius: 20px;
}

</style>
