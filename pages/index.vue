<template>
  <div class="container-fluid">
    <div class="row mobile">
      <component :is="currentComponent" />
      <div v-if="currentStep != 2" class="mobile-nav">
        <div class="but" @click="currentStep++" v-text="curTest[currentStep]" />
      </div>
      <div v-else class="mobile-nav">
        <Nuxt-link to="/done">
          <div
            class="but"
            @click="currentStep++"
            v-text="curTest[currentStep]"
          />
        </Nuxt-link>
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
  .mobile {
    display: flex;
  }

  .desktop {
    display: none;
  }

  .itogo {
    margin-left: 20px;
  }

  .button {
    display: none !important;
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

.mobile {
  padding: 20px;
}

.mobile-nav {
  margin-top: 100px;
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
}
</style>
