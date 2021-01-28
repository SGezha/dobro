<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-3 left-info">
        <div class="center">
          <div class="logo">
            <img src="/logo.png" alt="">
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
          <label for="c1">
            Я согласен на <a href="#">обработку персональных данных</a>
          </label>
        </div>
        <div class="row select-box">
          <div class="col-6">
            <h1>Вода</h1>
            <div class="inner-box">
              <div class="barel">
                <div class="main" @click="changeBarel(0)">
                  <img src="/path.png" class="bg-barel" alt="">
                  <div class="circle active" />
                  <h1>18,9 л</h1>
                  <h3>1 шт</h3>
                  <h2>220 ₽</h2>
                </div>
                <div class="colvo active">
                  <img src="/minus-circle.png" alt="" @click="minus">
                  <h1 v-text="info.colvo" />
                  <img src="/plus-circle.png" alt="" @click="plus">
                </div>
              </div>

              <div class="barel">
                <div class="main" @click="changeBarel(1)">
                  <img src="/path.png" class="bg-barel" alt="">
                  <div class="circle" />
                  <h1>1,5 л</h1>
                  <h3>6 шт</h3>
                  <h2>175 ₽</h2>
                </div>
                <div class="colvo">
                  <img src="/minus-circle.png" alt="" @click="minus">
                  <h1 v-text="info.colvo" />
                  <img src="/plus-circle.png" alt="" @click="plus">
                </div>
              </div>

              <div class="barel">
                <div class="main" @click="changeBarel(2)">
                  <img src="/path.png" class="bg-barel" alt="">
                  <div class="circle" />
                  <h1>0,5 л</h1>
                  <h3>12 шт</h3>
                  <h2>270 ₽</h2>
                </div>
                <div class="colvo">
                  <img src="/minus-circle.png" alt="" @click="minus">
                  <h1 v-text="info.colvo" />
                  <img src="/plus-circle.png" alt="" @click="plus">
                </div>
              </div>
            </div>
          </div>
          <div class="col-6 date">
            <h1>Дата и время доставки</h1>
            <div class="inner-date">
              <h2>ДЕНЬ</h2>
              <div class="den-box">
                <div
                  style="background: transparent;"
                  class="circle-den"
                  @click="
                    info.offset--
                    getDate()
                  "
                >
                  <img src="/left.png" alt="">
                </div>
                <div
                  v-for="(d, ind) in info.date"
                  :key="ind"
                  class="circle-den"
                  :class="{ active: d.active }"
                  @click="changeDate(ind)"
                >
                  <h1 :class="{ active: d.active }" v-text="d.data.day" />
                  <h2
                    :class="{ active: d.active, vihodnoi: d.vihodnoi }"
                    v-text="d.data.daysOfTheWeek"
                  />
                </div>
                <div
                  style="background: transparent;"
                  class="circle-den"
                  @click="
                    info.offset++
                    getDate()
                  "
                >
                  <img src="/right.png" alt="">
                </div>
              </div>

              <h2>ВРЕМЯ</h2>
              <div v-if="!info.selected.vihodnoi" class="time-box">
                <div class="time active" @click="changeTime(0)">
                  10:00 - 11:00
                </div>
                <div class="time" @click="changeTime(1)">
                  12:00 - 13:00
                </div>
                <div class="time" @click="changeTime(2)">
                  15:00 - 16:00
                </div>
              </div>

              <div v-else class="time-box">
                <div class="time active" @click="changeTime(0)">
                  12:00 - 13:00
                </div>
                <div class="time" @click="changeTime(1)">
                  15:00 - 16:00
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="itogo">
            <h1>Итого</h1>
            <h1>{{ info.summa * info.colvo }},<span>00 ₽</span></h1>
          </div>
          <div class="button">
            Заказать воду
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const daysOfTheWeek = ['ВС', 'ПН', 'ВТ', 'СР', 'ЧТ', 'ПТ', 'СБ']

export default {
  data () {
    return {
      info: {
        barel: 0,
        colvo: 1,
        date: [],
        selected: {},
        offset: 0,
        summa: 220
      }
    }
  },
  mounted () {
    this.getDate()
  },
  methods: {
    changeBarel (id) {
      const all = document.querySelectorAll('.circle')
      const colvo = document.querySelectorAll('.colvo')
      all.forEach((e) => {
        e.classList.remove('active')
      })
      colvo.forEach((e) => {
        e.classList.remove('active')
      })
      all[id].classList.add('active')
      colvo[id].classList.add('active')
      this.info.barel = id
      if (id === 0) { this.info.summa = 220 }
      if (id === 1) { this.info.summa = 175 }
      if (id === 2) { this.info.summa = 270 }
    },
    changeTime (id) {
      const all = document.querySelectorAll('.time')
      all.forEach((e) => {
        e.classList.remove('active')
      })
      all[id].classList.add('active')
    },
    changeDate (id) {
      this.info.date.forEach((e) => {
        e.active = false
      })
      this.info.date[id].active = true
      this.info.selected = this.info.date[id]
    },
    minus () {
      if (this.info.colvo > 0) {
        this.info.colvo--
      }
    },
    plus () {
      this.info.colvo++
    },
    getDisplay (month, day, year) {
      if (day > 31) {
        month += 1
        day -= 31
      }
      const d = new Date(year, month - 1, day)
      return { day, daysOfTheWeek: daysOfTheWeek[d.getDay()] }
    },
    getDate () {
      const Today = new Date()
      const d = Today.getDate() + this.info.offset
      const m = Today.getMonth() + 1
      const y = 2021
      this.info.date = []
      for (let i = 0; i < 6; i++) {
        const info = this.getDisplay(m, d + i, y)
        let vihodnoi = false
        if (info.daysOfTheWeek === 'ВС' || info.daysOfTheWeek === 'СБ') {
          vihodnoi = true
        }
        this.info.date.push({
          active: i === 0,
          data: info,
          vihodnoi
        })
      }
    }
  }
}
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
  border-bottom: 1px solid #d5dde0;
  padding: 10px;
  padding-left: 0;
  color: #455273;
}

.form-box input:focus {
  outline: none;
}

.form-box input::placeholder {
  color: #babdc2;
}

.check-box a {
  color: #418de8;
}

.check-box label {
  font-size: 12px;
}

.select-box {
  margin-top: 60px;
}

.inner-box {
  user-select: none;
  display: flex;
  align-items: center;
}

.barel {
  cursor: pointer;
  position: relative;
  width: 120px;
  margin-right: 20px;
  z-index: 1;
}

.main {
  cursor: pointer;
  position: relative;
  width: 120px;
  height: 160px;
  border-radius: 8px;
  z-index: 1;
  overflow: hidden;
  background: white;
}

.barel h1 {
  margin: 12px;
}

.barel h3 {
  font-size: 12px;
  margin: 12px;
}

.barel h2 {
  margin: 12px;
  margin-top: 60px;
  font-size: 16px;
  color: white;
}

.circle {
  width: 12px;
  height: 12px;
  background: #d5dde0;
  border-radius: 50%;
  position: absolute;
  right: 12px;
  top: 12px;
  transition: 0.3s ease;
}

.circle.active {
  background: #ffc369;
}

.bg-barel {
  left: 0;
  bottom: 0;
  position: absolute;
  width: 100%;
  z-index: -1;
}

.colvo {
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
}

.colvo.active {
  opacity: 1;
}

.colvo h1 {
  font-size: 16px;
}

.colvo img {
  width: 16px;
  height: 16px;
}

.inner-date h2 {
  color: #babdc2;
  font-size: 14px;
  margin: 15px 0;
}

.date {
  user-select: none;
}

.date h1 {
  margin-bottom: 10px;
}

.den-box {
  display: flex;
  justify-content: center;
  align-items: center;
}

.circle-den {
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: #e5edff;
  border-radius: 50%;
  overflow: hidden;
  cursor: pointer;
  margin-right: 8px;
  transition: 0.3s;
}

.circle-den.active {
  background: #ffc369;
}

.circle-den h1 {
  font-size: 20px;
  margin: 0;
  padding-top: 15px;
  line-height: 10px;
}

.circle-den h2 {
  font-size: 11px;
  margin-top: 6px;
  line-height: 10px;
}

h2.vihodnoi {
  color: #fd7562;
}

h1.active {
  color: white;
}

h2.active {
  color: white;
}

.circle-den img {
  width: 100%;
  height: 100%;
}

.time-box {
  display: flex;
  justify-content: center;
  align-items: center;
}

.time {
  font-size: 20px;
  color: #455273;
  padding: 10px 30px;
  background: #e5edff;
  font-weight: 700;
  border-radius: 30px;
  margin-right: 10px;
  cursor: pointer;
  transition: 0.3s ease;
}

.time.active {
  color: white;
  background: #ffc369;
}

.itogo {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #d5dde0;
  border-top: 1px dashed #d5dde0;
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

.button {
  padding: 10px 40px;
  color: white;
  background: #418DE8;
  font-size: 20px;
  border-radius: 30px;
  cursor: pointer;
  margin-top: 60px;
}
</style>
