<template>
  <div class="container-fluid">
    <div class="row mobile">
      <component :is="currentComponent" />
      <div v-if="curTest[currentStep] != undefined" class="mobile-nav">
        <div class="but" @click="currentStep++" v-text="curTest[currentStep]" />
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

<style>
@media (min-width: 320px) {
  .desktop {
    display: none;
  }
  .itogo {
    margin-left: 20px;
  }

  .left-info {
    margin-top: 100px;
    height: 100%;
    align-items: center;
  }
}

@media (min-width: 768px) {
  .desktop {
    display: flex;
  }
  .mobile {
    display: none;
  }
  .select-box {
    margin-top: 60px;
  }
  .button {
    display: block;
  }
}

.mobile {
  padding: 20px;
}

.mobile-nav {
  position: absolute;
  bottom: 50px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
}

.but {
  padding: 10px 40px;
  color: white;
  background: #418de8;
  font-size: 20px;
  border-radius: 30px;
  cursor: pointer;
}
</style>
