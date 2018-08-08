<template>
  <div class="tile">
    <div class="icon" :class="{enabled: enabled}">
      <img :src="icon">
    </div>
    <p class="text">{{ text }}</p>
    <p v-if="status !== ''" class="status">{{ status }}</p>
  </div>
</template>
<script>
export default {
  props: ["icon", "text", "status", "enabled"]
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
.icon {
  flex-grow: 1;
}
.tile {
  background: #f7f7f7;
  border-radius: 20px;
  width: 200px;
  margin: 7px;
  padding: 14px;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  cursor: pointer;
  transition: 300ms ease;
  flex-shrink: 0;
  &.normal {
    height: 101px;
  }
  &.big {
    height: 120px;
  }
  &:hover {
    background: #ffffff;
    box-shadow: 0 2px 6px 0 rgba(197, 186, 186, 0.5);
  }
  .text {
    margin: 0;
    font-family: $fontFamily;
    color: $textColor;
    font-size: 14px;
    letter-spacing: 0;
    text-align: left;
    font-weight: bold;
  }
  .status {
    margin: 4px 0 0 0;
    font-family: $fontFamily;
    font-size: 12px;
    color: #858585;
    letter-spacing: 0;
    text-align: left;
  }
}
</style>
