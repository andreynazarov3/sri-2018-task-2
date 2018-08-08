<template>
  <section class="main">
    <h1>Главное</h1>
    <div class="content">
      <div class="info">
        <h2>Привет, Геннадий!</h2>
        <p>Двери и окна закрыты, сигнализация включена.</p>
        <div class="temp">
          <div class="temp-wrapper">
          <div class="temp-item">
            <h3>Дома</h3>
            <p>+23</p>
          </div>
          <div class="temp-item">
            <h3>За окном</h3>
            <p>
              +19
              <img src="@/assets/img/cloud-drizzle.svg" alt="">
            </p>
          </div>
          </div>
        </div>
      </div>
      <div class="tiles">
        <img src="@/assets/img/double-arrow.svg" alt="" class="double-arrow">
        <div class="tiles-wrapper">
          <Tile 
            class="big"
            v-for="(item, index) in tiles"
            :key="index"
            :icon="item.icon"
            :text="item.text"
            :status="item.status"
            :enabled="item.enabled"
          />
          </div>
      </div>
    </div>
  </section>
</template>
<script>
import Tile from "@/components/elements/Tile";
export default {
  components: {
    Tile
  },
  data() {
    return {
      tiles: [
        {
          icon: require("@/assets/img/icon_temperature.svg"),
          text: "Philips Cooler",
          status: "Начнет охлаждать в 16:30",
          enabled: false
        },
        {
          icon: require("@/assets/img/icon_scheduled.svg"),
          text: "Xiaomi Yeelight LED Smart Bulb",
          status: "Включится в 17:00",
          enabled: false
        },
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "Включить свет в коридоре",
          status: "",
          enabled: true
        },
        {
          icon: require("@/assets/img/icon_temperature.svg"),
          text: "Набрать горячую ванну",
          status: "Начнётся в 18:00",
          enabled: true
        },
        {
          icon: require("@/assets/img/icon_temperature.svg"),
          text: "Сделать пол тёплым во всей квартире",
          status: "",
          enabled: true
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
.main {
  width: calc(50% - #{$sectionGutter * 2});
  @media #{$ipadPortrait} {
    width: calc(100% - #{$sectionGutter * 2});
  }
  @media #{$mobile} {
    width: calc(100% - #{($sectionGutter * 2) + $mobileHorizontalPadding});
  }
}
.content {
  height: $mainContentHeight;
  background-image: url(~@/assets/img/maxresdefault.jpg);
  background-size: cover;
  border-radius: 20px;
  display: flex;
  justify-content: space-between;
  overflow: hidden;
  @media #{$mobile} {
    flex-direction: column;
    height: auto;
  }
  .info {
    padding: 25px;
    h2 {
      font-family: $fontFamily;
      font-size: 27px;
      color: $textColor;
      margin: 0 0 6px 0;
    }
    > p {
      font-family: $fontFamily;
      font-size: 14px;
      color: $textColor;
      margin: 0;
    }
    .temp {
      margin: 25px 0 0 0;
      overflow: hidden;
      &-wrapper {
        display: flex;
        margin: 0 -9px;
      }
      &-item {
        margin: 0 9px;
        h3 {
          font-family: $fontFamily;
          margin: 0;
          font-size: 14px;
          color: #858585;
          font-weight: normal;
        }
        p {
          font-family: $fontFamily;
          font-weight: bold;
          font-size: 36px;
          color: $textColor;
          letter-spacing: 0;
          text-align: left;
          margin: 0;
        }
      }
    }
  }
  .tiles {
    position: relative;
    padding: 0 20px 0 0;
    overflow: hidden;
    height: 100%;
    flex-shrink: 0;
    .double-arrow {
      position: absolute;
      bottom: 12px;
      left: 50%;
      transform: translateX(-50%);
      @media #{$mobile} {
        display: none;
      }
    }
    @media #{$mobile} {
      height: auto;
      padding: 0 0 20px 0;
    }
    &-wrapper {
      padding: 25px 0 25px 20px;
      height: 100%;
      margin: -7px;
      overflow-y: scroll;
      flex-direction: column;
      display: flex;
      @media #{$mobile} {
        padding: 25px 0 0 20px;
        flex-direction: row;
        overflow-y: hidden;
        overflow-x: scroll;
      }
    }
  }
}
h1 {
  @extend %sectionH1;
}
</style>
