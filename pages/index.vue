<template>
  <div class="container-fluid">
    <div class="row mobile">
      <div class="form">
        <component :is="currentComponent" />
        <div v-if="currentStep == 0" class="mobile-nav">
          <div
            class="but"
            @click="currentStep++"
            v-text="curTest[currentStep]"
          />
        </div>
        <div v-if="currentStep == 1" class="mobile-nav">
          <div class="but" @click="checkForm()" v-text="curTest[currentStep]" />
        </div>
        <div v-if="currentStep == 2" class="mobile-nav">
          <div class="but" @click="submit" v-text="curTest[currentStep]" />
        </div>
      </div>
    </div>
    <div class="row desktop">
      <Title />
      <div class="col-md-8 col-sm-12 form">
        <Userinfo />
        <Dates />
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
      barel: 0,
      summa: 220,
      selectedTime: '10:00 - 11:00',
      curTest: ['Заказать воду', 'Далее', 'Заказать воду'],
      steps: [Title, Userinfo, Dates]
    }
  },
  computed: {
    currentComponent () {
      return this.steps[this.currentStep]
    }
  },
  methods: {
    submit () {
      window.location = window.location + 'done'
    },
    checkForm () {
      let valid = true
      const obj = { summa: this.summa, time: this.selectedTime }
      if (this.barel === 0) {
        obj.barel = '18,9 л'
      }
      if (this.barel === 1) {
        obj.barel = '1,5 л'
      }
      if (this.barel === 2) {
        obj.barel = '0,5 л'
      }
      const data = document.querySelectorAll('input')
      data.forEach((e, ind) => {
        if (ind > 3) {
          return
        }
        if (e.value === false || e.value === '') {
          valid = false
          e.style.borderBottom = '1px solid red'
        }
        if (
          e.placeholder === 'Почта' &&
          (!e.value.includes('@') || !e.value.includes('.'))
        ) {
          valid = false
        }
        obj[e.placeholder] = e.value
      })
      if (!document.querySelector('#c1').checked) {
        valid = false
      }
      console.log(valid)
      if (valid === true) {
        localStorage.setItem('form', JSON.stringify(obj))
        this.currentStep++
      }
    }
  }
}
</script>

<style>
@media (min-width: 320px) {
  body {
    background: #f5f8ff;
  }
  .mobile {
    display: flex;
  }

  .desktop {
    display: none;
  }

  .button {
    display: none !important;
  }

  .left-info {
    margin-top: 50px;
    height: 100%;
    align-items: center;
  }
}

@media (min-width: 768px) {
  body {
    background: #e9effc;
  }

  .desktop {
    display: flex;
  }

  .mobile {
    display: none;
  }

  .select-box {
    margin-top: 60px;
  }

  .form {
    width: 100%;
    background: #f5f8ff;
    border-radius: 6px;
    margin-top: 30px;
    margin-bottom: 30px;
    padding: 40px;
  }

  .button {
    display: block !important;
  }

  .left-info {
    width: 100%;
    height: 100vh !important;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin: 0;
  }
}

.mobile-nav {
  display: flex;
  justify-content: center;
  width: 100%;
}

.but {
  padding: 10px 40px;
  color: white;
  background: #418de8;
  font-size: 20px;
  border-radius: 30px;
  cursor: pointer;
  margin: 20px 0px;
}
</style>
