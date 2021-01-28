<template>
  <div class="col-md-3 col-sm-12 left-info">
    <div class="center">
      <div class="logo">
        <img src="/logo.png" alt="">
      </div>
      <h1>Чистая Вода</h1>
      <h2>
        Питьевая вода, предназначенная для ежедневного потребления, идеально
        подходит для кулеров. Закажите доставку воды и мы привезем её на дом или
        в офис.
      </h2>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {}
  }
}
</script>

<style>
.left-info {
  width: 100%;
  height: 100vh !important;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0;
  flex-direction: column;
}

.center {
  display: flex;
  justify-content: center;
  flex-direction: column;
  text-align: center;
}

.logo {
  margin: 20px auto;
  width: 130px;
  height: 130px;
  background: #fae1be;
  border-radius: 50%;
  overflow: hidden;
}

.logo img {
  width: 100%;
  height: 100%;
}

.center h1 {
  font-size: 26px;
  font-weight: 700;
  color: #455273;
}

.center h2 {
  margin: 40px auto;
  width: 50%;
  font-size: 14px;
  color: #818fb2;
}
</style>
