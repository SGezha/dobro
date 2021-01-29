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
            <h1>Бутьль 18,9 л</h1>
            <h2>1 шт</h2>
          </div>
          <div class="done-line line">
            <h1>12 февраля</h1>
            <h2>10:00 - 11:00</h2>
          </div>
          <div class="done-line line">
            <h1>Адрес доставки</h1>
            <h2>г. Самара, ул. Спортивная 24, офис 305</h2>
          </div>
          <div class="done-line">
            <h1>Телефон</h1>
            <h2>+7 (905) 606-40-04</h2>
          </div>
        </div>
        <div class="row">
          <div class="itogo">
            <h1>Итого</h1>
            <h1>220,<span>00 ₽</span></h1>
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
      steps: [Title, Userinfo, Dates]
    }
  },
  computed: {
    currentComponent () {
      return this.steps[this.currentStep]
    }
  }
}
</script>

<style scoped>
a:hover {
  color: white;
  outline: none;
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

.text-done {
  margin: 20px;
}

.text-done h2 {
  font-size: 22px;
  display: block;
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

.done-line h1 {
  margin: 0;
  font-size: 24px;
}

.done-line h2 {
  color: #babdc2;
  font-size: 20px;
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
  margin-left: 20px;
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

.button {
  padding: 10px 40px;
  color: white;
  background: #418de8;
  font-size: 20px;
  border-radius: 30px;
  cursor: pointer;
  margin-top: 60px;
  margin-left: 20px;
  display: none;
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
  .itogo {
    margin-left: 20px;
  }

  .left-info {
    display: none;
    margin-top: 100px;
    height: 100%;
    align-items: center;
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
}
</style>
