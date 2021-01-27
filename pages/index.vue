<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-3 left-info">
        <div class="center">
          <div class="logo">
            <img src="/logo.png" alt="" />
          </div>
          <h1>Чистая Вода</h1>
          <h2>
            Питьевая вода, предназначенная для ежедневного потребления, идеально
            подходит для кулеров. Закажите доставку воды и мы привезем её на дом
            или в офис.
          </h2>
        </div>
      </div>
      <div class="col-8 form">
        <h1>Заполните данные</h1>
        <div class="form-box">
          <input placeholder="ФИО" type="text">
          <input placeholder="Телефон" type="text">
          <input placeholder="Почта" type="text">
          <input placeholder="Адресс доставки" type="text">
        </div>
        <div class="check-box">
          <input id="c1" type="checkbox">
          <label for="c1">Я согласен на <a href="#">обработку персональных данных</a></label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.left-info {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
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

.form {
  width: 100%;
  height: 94vh;
  background: #f5f8ff;
  border-radius: 6px;
  margin-top: 30px;
  padding: 40px;
}

.form h1 {
  font-size: 24px;
  font-weight: 900;
  color: #455273;
  letter-spacing: 1.3px;
  margin-bottom: 40px;
}

.form-box {
  display: grid;
  grid-template-columns: 50% 50%;
}

.form-box input {
  margin-right: 80px;
  margin-bottom: 30px;
  background: transparent;
  border: none;
  border-bottom: 1px solid #D5DDE0;
  padding: 10px;
  padding-left: 0;
  color: #455273;
}

.form-box input:focus {
  outline: none;
}

.form-box input::placeholder {
  color: #BABDC2;}

.check-box a {
  color: #418DE8;
}

.check-box label {
  font-size: 12px;
}
</style>
