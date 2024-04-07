<template>
  <q-page class="flex flex-center results">
    <div class="q-pa-md">
      <div
        class="q-mb-lg"
        style="border-radius: 12px; background-color: #fee9d0"
      >
        <div
          class="block q-ma-xs"
          style="font-size: 3rem; color: #66987c"
          :key="item.label"
          v-for="(item, index) in result
            .sort((a, b) => b.value - a.value)
            .filter((item, index) => index < 1)"
        >
          {{ index + 1 }}º {{ item.label }}
        </div>
      </div>

      <div style="border-radius: 12px; background-color: #fee9d0">
        <div
          class="block text-center q-ma-xs"
          style="font-size: 1.5rem; color: #7a8f94"
          :key="item.label"
          v-for="(item, index) in result
            .sort((a, b) => b.value - a.value)
            .filter((item, index) => index < 3 && index > 0)"
        >
          {{ index + 2 }}º {{ item.label }}
        </div>
      </div>

      <div class="flex flex-center q-mt-md">
        <q-btn
          dense
          no-caps
          class="btn-details q-px-xl q-py-xs"
          label="detalhes"
          rounded
          @click="dialog = true"
          size="15px"
        />
      </div>
    </div>

    <div class="q-pa-lg full-width text-center flex flex-center">
      <q-btn
        dense
        no-caps
        class="btn-init q-px-xl q-py-xs"
        label="Refazer teste"
        rounded
        @click="backToHome"
        size="15px"
      />
    </div>

    <q-dialog v-model="dialog" persistent>
      <q-card style="min-width: 70%" class="results">
        <q-card-section class="text-h6"> Detalhes </q-card-section>
        <q-card-section>
          <div>
            <div
              class="block q-ma-xs"
              :key="item.label"
              v-for="item in result.sort((a, b) => b.value - a.value)"
            >
              {{ item.label }}: {{ item.value }}
            </div>
          </div>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn
            flat
            no-caps
            label="fechar"
            color="primary"
            @click="dialog = false"
          />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <span class="absolute" style="bottom: 5px; color: white">
      2024 - by IBVN
    </span>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import HolySpirit from 'src/assets/holy-spirit.json'

export default defineComponent({
  name: 'ResultPage',

  mounted () {
    const monitoring = JSON.parse(localStorage.getItem('monitoring'))
    this.result = monitoring
  },

  data () {
    return {
      HolySpirit,
      result: [],
      dialog: false
    }
  },

  methods: {
    backToHome () {
      this.$router.push('/')
    }
  }
})
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Dosis:wght@200..800&display=swap');

.results {
  font-family: 'Dosis', sans-serif;
}

.title {
  font-family: 'Dosis', sans-serif;
  font-style: normal;
  font-size: 3rem;
  color: #66987c;
}

.btn-init {
  bottom: 20px;
  width: 45%;
  margin: 0 5px;
  background-color: #66987c;
  color: #fee9d0;
}

.btn-finish {
  bottom: 20px;
  width: 45%;
  margin: 0 5px;
  background-color: #66987c;
  color: #fee9d0;
}

.btn-details {
  width: 45%;
  background-color: #fed285;
  color: #7a8f94;
}
</style>
