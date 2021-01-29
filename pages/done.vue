<template>
  <div class="container-fluid">
    <div class="row desktop">
      <Title />
      <div class="col-md-8 col-sm-12 form">
        <div class="done">
          <img class="done-img" src="/done.png" alt="">
          <h1>Заказ оформлен</h1>
        </div>
        <div class="done-info">
          <div class="done-line line">
            <h1>Бутыль {{ barel }}</h1>
            <h2>1 шт</h2>
          </div>
          <div class="done-line line">
            <h1>12 февраля</h1>
            <h2>{{ time }}</h2>
          </div>
          <div class="done-line line">
            <h1>Адрес доставки</h1>
            <h2>{{ adress }}</h2>
          </div>
          <div class="done-line">
            <h1>Телефон</h1>
            <h2>{{ phone }}</h2>
          </div>
        </div>
        <div class="itogo">
          <h1>Итого</h1>
          <h1>{{ summa }},<span>00 ₽</span></h1>
        </div>
        <div class="text-done">
          <h2>
            Ваш заказ <a href="#">№221</a> успешно оформлен. В ближайшее время
            по указанному телефону с Вами свяжется наш менеджер.
          </h2>
        </div>
        <Nuxt-link to="/" class="button">
          <a>Новый заказ</a>
        </Nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import Title from '@/components/title.vue'
import Userinfo from '@/components/userinfo.vue'
import Dates from '@/components/dates.vue'

export default {
  data () {
    return {
      Title,
      Userinfo,
      Date,
      currentStep: 0,
      curTest: ['Заказать воду', 'Далее', 'Заказать воду'],
      steps: [Title, Userinfo, Dates],
      summa: 220,
      barel: '18,9 л',
      time: '10:00 - 11:00',
      adress: '',
      phone: '',
      fio: '',
      email: ''
    }
  },
  mounted () {
    const info = JSON.parse(localStorage.getItem('form'))
    this.summa = info.summa
    this.barel = info.barel
    this.time = info.time
    this.adress = info.['Адресс доставки']
    this.phone = info.['Телефон']
    this.fio = info.['ФИО']
    this.email = info.['Почта']
  }
}
</script>

<style scoped>
a:hover {
  color: white;
  outline: none;
}

.text-done {
  margin: 10px 0px;
}

.done-line {
  padding-top: 20px;
  padding-bottom: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.line {
  border-bottom: 1px dashed #d5dde0;
}

.done {
  display: flex;
  align-items: center;
}

.done h1 {
  margin: 0;
  margin-left: 10px;
}

.done-img {
  height: 40px;
  display: inline-block;
}

.itogo {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-between;
  border-top: none;
  border-bottom: 1px solid #d5dde0;
  margin-top: 30px;
}

.itogo h1 {
  margin: 0;
  margin-bottom: 15px;
  font-size: 28px;
  font-weight: 900px;
  margin-top: 30px;
}

.itogo > h1 > span {
  color: #babdc2;
}

@media (min-width: 320px) {
  .desktop {
    display: flex;
  }
  .form {
    margin: 0;
  }
  .select-box {
    margin-top: 60px;
  }
  .button {
    display: block !important;
  }
  .left-info {
    margin: 0 !important;
  }

  .left-info {
    display: none;
    margin-top: 100px;
    height: 100%;
    align-items: center;
  }

  .done-info {
    display: flex;
    padding: 10px;
    justify-content: center;
    flex-direction: column;
    background: white;
    border-radius: 8px;
    margin: 0px;
    margin-top: 20px;
  }

  .done-line h1 {
    margin: 0;
    font-size: 16px;
  }

  .done-line h2 {
    color: #babdc2;
    font-size: 12px;
  }

  .button {
    padding: 10px 40px;
    color: white;
    background: #418de8;
    font-size: 20px;
    border-radius: 30px;
    cursor: pointer;
    margin: 20px auto;
    display: none;
  }

  .text-done h2 {
    margin: 30px 0;
    font-size: 18px;
    display: block;
    text-align: center;
  }
}

@media (min-width: 768px) {
  .desktop {
    display: flex;
  }
  .select-box {
    margin-top: 60px;
  }
  .button {
    display: block !important;
  }
  .left-info {
    margin: 0 !important;
    display: flex;
  }
  .form {
    margin-top: 30px;
    margin-bottom: 30px;
  }

  .done-info {
    display: flex;
    padding: 20px;
    justify-content: center;
    flex-direction: column;
    background: white;
    border-radius: 8px;
    margin: 10px;
    margin-top: 40px;
  }

  .done-line h1 {
    margin: 0;
    font-size: 24px;
  }

  .done-line h2 {
    color: #babdc2;
    font-size: 20px;
  }

  .button {
    padding: 10px 40px;
    color: white;
    background: #418de8;
    font-size: 20px;
    border-radius: 30px;
    cursor: pointer;
    margin-top: 60px;
    display: none;
  }

  .text-done h2 {
    font-size: 22px;
    display: block;
    text-align: left;
  }
}
</style>
