<template>
<div class="modal-overlay">
  <div class="modal">
    <div class="content">
      <div class="heading">
          <div class="text">
            <h1>
              Elgato Eve Degree Connected
            </h1>
            <p>Elgato Eve Degree Connected</p>
          </div>
          <div class="temp">
            <span>+23</span>
            <img src="@/assets/img/icon_temperature.svg">
          </div>
      </div>
      <div class="tags">
        
      </div>
      <div class="controller">
        <div class="bar">
          <span class="low">-10</span>
          <span class="high">30</span>
        </div>
      </div>
    </div>
    <div class="buttons">
      <button>Применить</button>
      <button>Закрыть</button>
    </div>
  </div>
</div>
</template>
<style lang="scss" scoped>
.modal {
  width: 630px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  .content {
    background: white;
    border-radius: 20px;
  }
  &-overlay {
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
