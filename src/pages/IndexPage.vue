<template>
  <q-page class="flex flex-center">
    <div class="text-center">
      <Vue3Lottie
        :loop="false"
        :speed="0.8"
        :animationData="HolySpirit"
        height="50vh"
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
        size="35px"
      />
    </div>

    <span class="absolute" style="bottom: 5px; color: white">
      2024 - by Cáliton
    </span>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import HolySpirit from 'src/assets/holy-spirit.json'

export default defineComponent({
  name: 'IndexPage',

  data () {
    return {
      HolySpirit
    }
  }
})
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Jua&display=swap');

.title {
  font-style: normal;
  font-size: 4rem;
  color: #66987c;
}

.btn-init {
  bottom: 20px;
  width: 80%;
  background-color: #66987c;
  color: #fee9d0;
}
</style>
