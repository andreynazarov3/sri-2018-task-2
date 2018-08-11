<template>
  <section class="favorites">
    <div class="heading">
      <h1>Избранные сценарии</h1>
      <div class="arrows">
         <prev class="arrow" />
         <next class="arrow" />
      </div>
    </div>
    <div class="tiles">
        <div class="tiles-col">
          <div class="tiles-col-wrapper">
          <Tile 
            class="normal"
            v-for="(item, index) in [tiles[0], tiles[1], tiles[2]]"
            :key="index"
            :icon="item.icon"
            :text="item.text"
            :status="item.status"
            :enabled="item.enabled"
            @click.native="handleClick(item)"
          />
          </div>
        </div>
        <div class="tiles-col">
          <div class="tiles-col-wrapper">
          <Tile 
            class="normal"
            v-for="(item, index) in [tiles[2], tiles[3], tiles[0]]"
            :key="index"
            :icon="item.icon"
            :text="item.text"
            :status="item.status"
            :enabled="item.enabled"
            @click.native="handleClick(item)"
          /></div>
        </div>
        <div class="tiles-col">
          <div class="tiles-col-wrapper">
          <Tile 
            class="normal"
            v-for="(item, index) in [tiles[4]]"
            :key="index"
            :icon="item.icon"
            :text="item.text"
            :status="item.status"
            :enabled="item.enabled"
            @click.native="handleClick(item)"
          />
        </div>
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
          text: "Выключить весь свет в доме и во дворе",
          status: "",
          enabled: true,
          type: "light"
        },
        {
          icon: require("@/assets/img/icon_scheduled.svg"),
          text: "Я ухожу",
          status: "",
          enabled: false,
          type: "light"
        },
        {
          icon: require("@/assets/img/icon_sun.svg"),
          text: "Включить свет в коридоре",
          status: "",
          enabled: true,
          type: "light"
        },
        {
          icon: require("@/assets/img/icon_temperature.svg"),
          text: "Набрать горячую ванну",
          status: "Начнётся в 18:00",
          enabled: true,
          type: "temp"
        },
        {
          icon: require("@/assets/img/icon_temperature.svg"),
          text: "Сделать пол тёплым во всей квартире",
          status: "",
          enabled: true,
          type: "temp"
        }
      ]
    };
  },
  methods: {
    handleClick(item) {
      switch (item.type) {
        case "light":
          return this.$emit("lightModalOpen", item);
        case "temp":
          return this.$emit("tempModalOpen", item);
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
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
  width: calc(50% - #{$sectionGutter * 2});
  display: flex;
  flex-direction: column;
  @media #{$ipadPortrait} {
    width: calc(100% - #{$sectionGutter * 2});
  }
}

h1 {
  @extend %sectionH1;
}
.tiles {
  height: $mainContentHeight;
  display: flex;
  overflow-x: scroll;
  @media #{$mobile} {
    height: auto;
  }
  &-col {
    overflow: hidden;
    flex-shrink: 0;
    margin-right: 14px;
    &-wrapper {
      margin: -7px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      @media #{$mobile} {
        flex-direction: row;
      }
    }
  }
}
</style>
