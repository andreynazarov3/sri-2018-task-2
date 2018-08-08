<template>
  <section class="favorites">
    <div class="heading">
      <div class="headingAndTags">
        <h1>Избранные устройства</h1>
        <div class="tags">
          <div class="tags-wrapper">
            <a href="#" class="active">Все<prev class="arrow active" /></a>
            <a href="#">Кухня</a>
            <a href="#">Зал</a>
            <a href="#">Лампочки</a>
            <a href="#">Камеры</a>
          </div>
        </div>
      </div>
      <div class="arrows">
         <prev class="arrow" />
         <next class="arrow" />
      </div>
    </div>
    <div class="tiles">
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
  </section>
</template>
<script>
import Tile from "@/components/elements/Tile";
import next from "@/components/svg/next";
import prev from "@/components/svg/prev";
export default {
  components: {
    Tile,
    prev,
    next
  },
  data() {
    return {
      tiles: [
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "Xiaomi Yeelight LED Smart Bulb",
          status: "Включено",
          enabled: true
        },
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "D-Link Omna 180 Cam",
          status: "Включится в 17:00",
          enabled: false
        },
        {
          icon: require("@/assets/img/icon_temperature.svg"),
          text: "Elgato Eve Degree Connected",
          status: "Выключено до 17:00",
          enabled: false
        },
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "LIFX Mini Day & Dusk A60 E27",
          status: "Включится в 17:00",
          enabled: false
        },
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "Xiaomi Mi Air Purifier 2S",
          status: "Включено",
          enabled: true
        },
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "Philips Zhirui",
          status: "Выключено",
          enabled: false
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
.headingAndTags {
  display: flex;
  align-items: center;
  padding: 30px 0 20px 0;
}
.tags {
  overflow: hidden;
  &-wrapper {
    margin: 0 -5px;
    display: flex;
  }
  a {
    display: flex;
    align-items: center;
    line-height: 30px;
    margin: 0 5px;
    background: #f7f7f7;
    border-radius: 20px;
    font-family: $fontFamily;
    font-size: 13px;
    color: #000000;
    text-align: left;
    text-decoration: none;
    font-weight: bold;
    height: 30px;
    padding: 0 15px;
    @media screen and (max-width: 767px) {
      display: none;
    }
    .arrow {
      transform: rotateZ(-90deg);
      width: 10px;
      margin-left: 5px;
      display: none;
      @media screen and (max-width: 767px) {
        display: block;
      }
    }
    &.active {
      background: #ffd93e;
      @media screen and (max-width: 767px) {
        display: flex;
      }
    }
  }
}
.arrows {
  display: flex;
  margin-right: 20px;
  @media #{$mobile} {
    display: none;
  }
  .arrow {
    display: block;
    margin: 8px;
    width: 14px;
    cursor: pointer;
  }
}
.heading {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}
.favorites {
  width: calc(100% - #{$sectionGutter * 2});
  display: flex;
  flex-direction: column;
}
h1 {
  @extend %sectionH1;
  padding: 0;
  margin-right: 13px;
}
.tiles {
  overflow: hidden;
  padding-bottom: 15px;
  &-wrapper {
    display: flex;
    margin: -7px;
    justify-content: flex-start;
    overflow-x: scroll;
  }
}
</style>
