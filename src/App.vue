<template>
  <div id="app">
    <nav-bar />
    <main>
      <div class="app-wrapper">
        <Main @lightModalOpen="(item) => openModal(item)" @tempModalOpen="(item) => openModal(item)"/>
        <Scenarios @lightModalOpen="(item) => openModal(item)" @tempModalOpen="(item) => openModal(item)"/>
        <Devices @lightModalOpen="(item) => openModal(item)" @tempModalOpen="(item) => openModal(item)"/>
      </div>
    </main>
    <my-footer />
    <modal-temp :item="item" v-if="tempModalActive" @dismountTemp="tempModalActive = false" />
    <modal-light :item="item" v-if="lightModalActive" @dismountLight="lightModalActive = false" />
  </div>
</template>
<script>
import {
  MyFooter,
  NavBar,
  Main,
  Scenarios,
  Devices,
  ModalTemp,
  ModalLight
} from "./components";
export default {
  methods: {
    openModal(item) {
      this.item = item;
      switch (item.type) {
        case "light":
          return (this.lightModalActive = true);
        case "temp":
          return (this.tempModalActive = true);
      }
    }
  },
  data() {
    return {
      item: null,
      tempModalActive: false,
      lightModalActive: false
    };
  },
  components: {
    NavBar,
    Main,
    Scenarios,
    Devices,
    MyFooter,
    ModalTemp,
    ModalLight
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
