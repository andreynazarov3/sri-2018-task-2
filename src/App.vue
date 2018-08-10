<template>
  <div id="app">
    <nav-bar />
    <main>
      <div class="app-wrapper">
        <Main />
        <Scenarios />
        <Devices @tempModalOpen="tempModalActive = true"/>
      </div>
    </main>
    <my-footer />
    <modal-temp v-if="tempModalActive" @dismountTemp="tempModalActive = false" />
  </div>
</template>
<script>
import {
  MyFooter,
  NavBar,
  Main,
  Scenarios,
  Devices,
  ModalTemp
} from "./components";
export default {
  data() {
    return {
      tempModalActive: false
    };
  },
  components: {
    NavBar,
    Main,
    Scenarios,
    Devices,
    MyFooter,
    ModalTemp
  }
};
</script>

<style lang="scss">
@import "@/assets/scss/vars.scss";
html,
body,
#app {
  min-height: 100vh;
}
#app {
  display: flex;
  flex-direction: column;
}
main {
  overflow: hidden;
  flex-grow: 1;
  padding-top: $appTopPadding;
  @media #{$mobile} {
    padding-top: $mobileTopPadding;
  }
}
section {
  margin: 0 $sectionGutter;
}
.app-wrapper {
  padding: 0 0 0 $appHorizontalPadding;
  display: flex;
  flex-wrap: wrap;
  margin: 0 -#{$sectionGutter};
  @media #{$mobile} {
    padding: 0 0 0 $mobileHorizontalPadding;
  }
}
</style>
