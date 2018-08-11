<template>
<div class="modal-overlay">
  <transition name="scale" v-on:after-leave="$emit('dismountLight')">
    <div v-if="mounted" class="modal">
      <div class="content">
        <div class="heading">
            <div class="text">
              <h1>
                {{ item.text }}
              </h1>
              <p> {{ item.status }}</p>
            </div>
            <div class="temp">
              <img src="@/assets/img/icon_sun.svg">
            </div>
        </div>
        <div class="tags">
            <div class="tags-wrapper">
              <a href="#" class="active">Вручную</a>
              <a href="#">Дневной свет</a>
              <a href="#">Вечерний свет</a>
              <a href="#">Рассвет</a>
            </div>
          </div>
        <div class="controller">
          <div class="bar" ref="bar">
            <div class="selector" ref="selector"></div>
            <span class="low"><img src="@/assets/img/icon_sun_white.svg"></span>
            <span class="high"><img src="@/assets/img/icon_sun_white.svg"></span>
          </div>
        </div>
      </div>
      <div class="buttons">
        <button @click="mounted = false" class="yellow">Применить</button>
        <button @click="mounted = false">Закрыть</button>
      </div>
    </div>
  </transition>
</div>
</template>
<script>
export default {
  props: ["item"],
  data() {
    return { mounted: false };
  },
  mounted() {
    this.mounted = true;
    this.$nextTick(function() {
      window.Draggable.create(this.$refs.selector, {
        type: "x,y",
        edgeResistance: 1,
        bounds: this.$refs.bar
      });
    });
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/vars.scss";
.scale-enter-active,
.scale-leave-active {
  transform: scale(1);
  transition: all 300ms ease;
}
.scale-enter,
.scale-leave-to {
  opacity: 0;
  transform: scale(0.4);
}
.buttons {
  margin: 20px 0 0 0;
  display: flex;
  justify-content: space-between;
  @media #{$mobile} {
    flex-direction: column;
  }
  button {
    font-family: $fontFamily;
    font-weight: bold;
    font-size: 18px;
    background: white;
    border: none;
    border-radius: 20px;
    width: calc(50% - 10px);
    height: 60px;
    cursor: pointer;
    @media #{$mobile} {
      width: 100%;
      margin-bottom: 20px;
    }
    &.yellow {
      background: #ffd93e;
    }
  }
}
.controller {
  position: relative;
  margin: 25px 0 0 0;
  @media #{$mobile} {
    height: 336px;
  }
  .bar {
    box-sizing: border-box;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
    height: 60px;
    width: 100%;
    background-image: linear-gradient(-85deg, #ffe682 2%, #ff9e00 98%);
    border-radius: 30px;
    padding: 0 20px;
    @media #{$mobile} {
      position: absolute;
      width: 336px;
      transform: rotate(90deg);
      transform-origin: left;
      left: calc(50%);
      top: -30px;
    }
    span {
      font-family: $fontFamily;
      color: white;
      font-size: 18px;
      font-weight: bold;
      @media #{$mobile} {
        transform: rotate(-90deg);
      }
    }
    .selector {
      position: absolute;
      left: 50%;
      border-radius: 50%;
      border: 4px solid white;
      height: 56px;
      width: 56px;
    }
  }
}
.tags {
  overflow: hidden;
  &-wrapper {
    margin: 0 -5px;
    display: flex;
    overflow: auto;
  }
  a {
    display: flex;
    align-items: center;
    flex-shrink: 0;
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
    &.active {
      background: #ffd93e;
    }
  }
}
.modal {
  margin: auto;
  width: 630px;
  max-width: calc(100% - 40px);
  padding: 20px 0;
  .content {
    background: white;
    border-radius: 20px;
    padding: 25px;
    .heading {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;

      h1 {
        font-family: $fontFamily;
        margin: 0;
        font-size: 27px;
        color: $textColor;
        font-weight: bold;
      }
      p {
        font-family: $fontFamily;
        margin: 6px 0 20px 0;
        font-size: 14px;
        color: $textColor;
      }
    }
    .temp {
      display: flex;
      align-items: center;
      @media #{$mobile} {
        display: none;
      }
      span {
        font-family: $fontFamily;
        margin: 0;
        font-size: 36px;
        color: $textColor;
        letter-spacing: 0;
        font-weight: bold;
      }
      img {
        height: 40px;
      }
    }
  }
  &-overlay {
    overflow-y: auto;
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 9999;
  }
}
</style>
