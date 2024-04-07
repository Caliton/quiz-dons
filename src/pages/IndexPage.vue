<template>
  <q-page class="flex flex-center">
    <div class="text-center">
      <Vue3Lottie
        :loop="false"
        :speed="0.8"
        :animationData="HolySpirit"
        height="40vh"
      />
      <span class="title">Quiz Dons</span>
    </div>

    <div class="q-pa-lg full-width text-center flex flex-center">
      <q-btn
        dense
        no-caps
        class="btn-init q-px-xl q-py-xs"
        label="Iniciar"
        rounded
        @click="$router.push('/quiz')"
        size="20px"
      />

      <q-btn
        v-if="isResult"
        dense
        no-caps
        class="btn-details q-px-xl q-py-xs"
        label="ver resultado anterior"
        rounded
        @click="$router.push('/result')"
      />
    </div>

    <span class="absolute" style="bottom: 5px; color: white">
      2024 - by IBVN
    </span>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import HolySpirit from 'src/assets/holy-spirit.json'

export default defineComponent({
  name: 'IndexPage',

  mounted () {},

  data () {
    return {
      HolySpirit,
      isResult: !!localStorage.getItem('monitoring')
    }
  }
})
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Jua&display=swap');

.title {
  font-style: normal;
  font-size: 3rem;
  color: #66987c;
}

.btn-init {
  bottom: 20px;
  width: 80%;
  background-color: #66987c;
  color: #fee9d0;
}

.btn-details {
  background-color: #fed285;
  color: #7a8f94;
}
</style>
