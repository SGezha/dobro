<template>
  <div>
    <h1>Заполните данные</h1>
    <div class="row form-box">
      <div class="col-lg-6 col-md-12">
        <input placeholder="ФИО" type="text">
        <input placeholder="Почта" type="email">
      </div>
      <div class="col-lg-6 col-md-12">
        <input
          v-model="info.phone"
          v-mask="'+7 (###) ###-##-##'"
          placeholder="Телефон"
          type="text"
        >
        <input placeholder="Адресс доставки" type="text">
      </div>
    </div>
    <div class="check-box">
      <input id="c1" type="checkbox">
      <label for="c1">
        Я согласен на <a href="#">обработку персональных данных</a>
      </label>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'

import { VueMaskDirective } from 'v-mask'
Vue.directive('mask', VueMaskDirective)

export default {
  data () {
    return {
      info: {
        phone: ''
      }
    }
  }
}
</script>

<style>
@media (min-width: 320px) {
  .form {
    width: 100%;
    background: #f5f8ff;
    margin: 0;
    padding: 10px;
  }

  .form h1 {
    font-size: 1.5rem;
    font-weight: 900;
    color: #455273;
    letter-spacing: 1.3px;
  }

  .check-box label {
    font-size: 12px !important;
  }
}

@media (min-width: 768px) {
  .form {
    width: 100%;
    background: #f5f8ff;
    border-radius: 6px;
    margin-top: 30px;
    margin-bottom: 30px;
    padding: 40px;
  }

  .form h1 {
    font-size: 1.5rem;
    font-weight: 900;
    color: #455273;
    letter-spacing: 1.3px;
    margin-bottom: 40px;
  }

  .check-box label {
    font-size: 14px !important;
  }
}

.form-box input {
  width: 100%;
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
</style>
