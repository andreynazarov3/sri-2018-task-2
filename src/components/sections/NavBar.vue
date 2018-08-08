<template>
  <header>
    <a class="logo">
      <img src="@/assets/img/Яндекс_Дом@1x.png" srcset="@/assets/img/Яндекс_Дом@1x.png 1x, @/assets/img/Яндекс_Дом@1x.png 2x" alt="Яндекс Дом">
    </a>
    <nav>
      <button class="ham"><img src="@/assets/img/ham.svg"></button>
      <div class="nav-wrapper">
      <a v-for="(item, index) in items" :key="index" href="#" :class="{active: item.active}">
        {{item.name}}
      </a>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          name: "Сводка",
          active: true
        },
        {
          name: "Устройства",
          active: false
        },
        {
          name: "Сценарии",
          active: false
        }
      ]
    };
  }
};
</script>
<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
.ham {
  background: none;
  border: none;
  display: none;
  padding: 0 20px;
  img {
    display: block;
  }
  @media #{$mobile} {
    display: block;
  }
}
nav {
  overflow: hidden;
  .nav-wrapper {
    display: flex;
    margin: 0 -13px;
    @media #{$mobile} {
      display: none;
    }
  }
  a {
    text-decoration: none;
    opacity: 0.6;
    font-family: Arial, sans-serif;
    font-size: 16px;
    color: $textColor;
    line-height: 20px;
    font-weight: bold;
    margin: 0 13px;
    &.active {
      opacity: 1;
    }
  }
}
header {
  width: 100%;
  padding: $headerVerticalPadding 0 $headerVerticalPadding $appHorizontalPadding;
  background: white;
  border-bottom: 1px solid #f0f0f0;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  z-index: 1;
  @media #{$mobile} {
    padding: $headerMobileVerticalPadding 0 $headerMobileVerticalPadding
      $mobileHorizontalPadding;
    justify-content: space-between;
    width: calc(100% - #{$mobileHorizontalPadding});
  }
}
.logo {
  margin-right: 52px;
  img {
    width: 108px;
    height: $logoHeight;
    display: block;
  }
}
</style>
