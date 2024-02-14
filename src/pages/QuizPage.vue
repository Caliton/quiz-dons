<template>
  <div class="q-pa-md flex flex-center">
    {{ myGifts[0].label }}
    <q-linear-progress
      stripe
      rounded
      size="20px"
      :value="progress"
      color="warning"
      class="q-mb-md"
    >
      <div
        class="absolute-full flex flex-center"
        style="color: #7a8f94; font-size: 0.7rem"
      >
        {{ currentQuestion }} / 35
      </div>
    </q-linear-progress>

    <div class="area-questions q-mb-lg" style="background-color: ">
      <span class="inline-block">
        {{ questions[currentQuestion - 1].id }})
        {{ questions[currentQuestion - 1].label }}
      </span>
    </div>

    <div class="full-width">
      <div
        class="q-ml-md q-mb-sm block full-width"
        :key="item.value"
        v-for="item of alternative"
      >
        <q-btn
          class="alternatives"
          :label="item.label"
          :style="item.style"
          rounded
          no-caps
          @click="setAnswer(item.value)"
        />
      </div>
    </div>

    <div>
      <div :key="item.label" v-for="item in asdf">
        {{ item.label }}: {{ item.value }}
      </div>
    </div>

    <div
      class="full-width flex justify-between absolute q-px-lg"
      style="bottom: 20px"
    >
      <q-btn
        class="btn-back"
        style="background-color: #fee9d0; color: #7a8f94"
        @click="backQuestion"
        rounded
        label="voltar"
        no-caps
      />
      <q-btn
        class="btn-next"
        style="background-color: #66987c; color: #fee9d0"
        rounded
        @click="nextQuestion"
        label="Avancar"
        no-caps
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'QuizPage',

  data () {
    return {
      currentQuestion: 1,
      answers: [],

      results: {
        1: 0,
        2: 0,
        3: 0,
        4: 0,
        5: 0,
        6: 0,
        7: 0
      },

      alternative: [
        {
          value: 0,
          label: 'Nao sou eu',
          style: 'background-color: #FEE9D0; color: #7A8F94'
        },
        {
          value: 1,
          label: 'Sou eu um pouco',
          style: 'background-color: #FED285; color: #7A8F94'
        },
        {
          value: 2,
          label: 'Sou eu bastante',
          style: 'background-color: #FEA485; color: #FEE9D0'
        },
        {
          value: 3,
          label: 'Sou eu exatamente',
          style: 'background-color: #66987C; color: #FEE9D0'
        }
      ],

      gifts: [
        {
          id: 1,
          label: 'Profecia',
          description:
            'Fala a verdade abertamente, pois seu intuito é levar o pecador ao arrependimento e adorar a Deus.',
          questions: [1, 8, 15, 22, 29]
        },
        {
          id: 2,
          label: 'Serviço',
          description:
            'Busca o interesse dos outros e não o seu; sacrificando muitas vezes a si mesmo.',
          questions: [2, 9, 16, 23, 30]
        },
        {
          id: 3,
          label: 'Ensino',
          description:
            'Procura usar a palavra de Deus de forma clara e convincente, crê que a palavra de Deus sempre cumpre o seu propósito.',
          questions: [3, 10, 17, 24, 31]
        },
        {
          id: 4,
          label: 'Exortação',
          description:
            'Seu objetivo é atingir o coração do pecador e do irmão com quem trabalha para encorajá-lo, incentivá-lo e aconselhá-lo, para que aquele com quem trabalha vem a obedecer a Deus.',
          questions: [4, 11, 18, 25, 32]
        },
        {
          id: 5,
          label: 'Contribuição',
          description:
            'É sensível às necessidades dos outros e da Igreja; está sempre pronto para contribuir mesmo diante de sua pobreza.',
          questions: [5, 12, 19, 26, 33]
        },
        {
          id: 6,
          label: 'Liderança',
          description:
            'É capaz de distribuir tarefas de modo que a obra seja feita com eficiência e haja resultados palpáveis.',
          questions: [6, 13, 20, 27, 34]
        },
        {
          id: 7,
          label: 'Misericórdia',
          description:
            'Consegue ser sensível às necessidades dos outros, e sempre está disposto a ajudar pessoalmente a cada um.',
          questions: [7, 14, 21, 28, 35]
        }
      ],

      questions: [
        {
          id: 1,
          gifts: [1],
          answer: 0,
          label:
            'Fala a verdade abertamente, pois seu intuito é levar o pecador ao arrependimento e adorar a Deus.'
        },
        {
          id: 2,
          gifts: [2],
          answer: 0,
          label:
            'Busca o interesse dos outros e não o seu; sacrificando muitas vezes a si mesmo.'
        },
        {
          id: 3,
          gifts: [3],
          answer: 0,
          label:
            'Procura usar a palavra de Deus de forma clara e convincente, crê que a palavra de Deus sempre cumpre o seu propósito.'
        },
        {
          id: 4,
          gifts: [4],
          answer: 0,
          label:
            'Seu objetivo é atingir o coração do pecador e do irmão com quem trabalha para encorajá-lo, incentivá-lo e aconselhá-lo, para que aquele com quem trabalha vem a obedecer a Deus.'
        },
        {
          id: 5,
          gifts: [5],
          answer: 0,
          label:
            'É sensível às necessidades dos outros e da Igreja; está sempre pronto para contribuir mesmo diante de sua pobreza.'
        },
        {
          id: 6,
          gifts: [6],
          answer: 0,
          label:
            'É capaz de distribuir tarefas de modo que a obra seja feita com eficiência e haja resultados palpáveis.'
        },
        {
          id: 7,
          gifts: [7],
          answer: 0,
          label:
            'Consegue ser sensível às necessidades dos outros, e sempre está disposto a ajudar pessoalmente a cada um.'
        },
        {
          id: 8,
          gifts: [1],
          answer: 0,
          label:
            'Está sempre pronto a denunciar o pecado, para que o pecador chegue ao pleno arrependimento, assim como fez Jesus e João Batista.'
        },
        {
          id: 9,
          gifts: [2],
          answer: 0,
          label:
            'Procura o bem coletivo, de modo que todo o seu trabalho seja para a glória de Deus'
        },
        {
          id: 10,
          gifts: [3],
          answer: 0,
          label:
            'É estudioso das Escrituras, pois quer ser estar apto para manejá-la bem.'
        },
        {
          id: 11,
          gifts: [4],
          answer: 0,
          label:
            'Está sempre disposto a dar uma segunda chance àqueles que porventura venham a falhar; e procura ajudá-los para restaurá-los.'
        },
        {
          id: 12,
          gifts: [5],
          answer: 0,
          label:
            'Está pronto para ajudar nas necessidades da Igreja e sempre se mostra voluntário seja em campanhas, sociais, missões ou alguma necessidade específica da Igreja.'
        },
        {
          id: 13,
          gifts: [6],
          answer: 0,
          label:
            'Em todos os lugares em que é colocado tende a assumir a liderança e a exerce sem constrangimento, mas de boa vontade.'
        },
        {
          id: 14,
          gifts: [7],
          answer: 0,
          label:
            'Quando vê alguém com alguma necessidade material e capaz de sacrificar-se para ajudá-lo em sua pobreza.'
        },
        {
          id: 15,
          gifts: [1],
          answer: 0,
          label:
            'Expõe a palavra de Deus de forma clara brilhante, fascinante e irresistível.'
        },
        {
          id: 16,
          gifts: [2],
          answer: 0,
          label:
            'Procura fazer as coisas, não para ser visto pelos homens, mas pelo prazer de estar sendo útil a obra de Deus.'
        },
        {
          id: 17,
          gifts: [3],
          answer: 0,
          label:
            'É confiante no poder do Espírito Santo para operar através da sua palavra, e procura expô-la o mais claro possível.'
        },
        {
          id: 18,
          gifts: [4],
          answer: 0,
          label:
            'Está pronto para encorajar e confirmar àqueles que estão passando por alguma tribulação'
        },
        {
          id: 19,
          gifts: [5],
          answer: 0,
          label:
            'Não fica só no querer ajudar; sempre faz algo que contribui para suprir as necessidades de outros.'
        },
        {
          id: 20,
          gifts: [6],
          answer: 0,
          label:
            'Se estiver no meio de pessoas com opiniões diferentes, mas sabe que sua idéia é melhor, tende a convencer os outros, e se não consegue, é humilde para se submeter e servir.'
        },
        {
          id: 21,
          gifts: [7],
          answer: 0,
          label:
            'Gosta de incentivar as pessoas enfermas e encorajá- las, tem prazer em visitá-las seja em casa ou hospital.'
        },
        {
          id: 22,
          gifts: [1],
          answer: 0,
          label:
            'Usa a palavra de Deus com intuito que todos sejam por ela julgados e convencidos do pecado.'
        },
        {
          id: 23,
          gifts: [2],
          answer: 0,
          label:
            'Fica feliz quando solicitado a colaborar com a obra, mesmo sem estar na liderança.'
        },
        {
          id: 24,
          gifts: [3],
          answer: 0,
          label:
            'É apegado à palavra fiel, é apegado à doutrina e não tem problemas de passar horas estudando e meditando na mesma.'
        },
        {
          id: 25,
          gifts: [4],
          answer: 0,
          label:
            'Mesmo que usa pregação visa sempre, atingir a alma e o espírito, para que haja reação positiva e todos sejam firmes.'
        },
        {
          id: 26,
          gifts: [5],
          answer: 0,
          label:
            'Administra seu dinheiro, mesmo quando pouco, de modo que sempre separa uma parte para a obra de Deus.'
        },
        {
          id: 27,
          gifts: [6],
          answer: 0,
          label:
            'Sabe que muitas vezes as pessoas o seguem, por isso procura viver de modo irrepreensível, pois não quer ser pedra de tropeço a obra de Deus e sim benção.'
        },
        {
          id: 28,
          gifts: [7],
          answer: 0,
          label:
            'É uma pessoa de oração; e nunca se esquece dos fracos espiritualmente, dos doentes, e daqueles que sofrem.'
        },
        {
          id: 29,
          gifts: [1],
          answer: 0,
          label:
            'Expõem a palavra de Deus abertamente para que sejam manifestos os segredos do coração'
        },
        {
          id: 30,
          gifts: [2],
          answer: 0,
          label:
            'Gosta de aliviar a carga das pessoas que ocupam posição chave para que possam ocupar mais em sua tarefa principal.'
        },
        {
          id: 31,
          gifts: [3],
          answer: 0,
          label:
            'Envolve-se também no Evangelismo, mas sempre é minucioso e preciso na exposição do Evangelho e nunca fica satisfeito só com a decisão do pecador, depois disso gosta de trabalhar como discipulador.'
        },
        {
          id: 32,
          gifts: [4],
          answer: 0,
          label:
            'Confia na ação do Espírito Santo, mesmo quando ele mesmo passa por alguma tribulação; pois sabe que poderá usar aquela experiência para ajudar outros e incentivá-los a serem perseverantes; sabe que o Espírito Santo é chamado de Consolador.'
        },
        {
          id: 33,
          gifts: [5],
          answer: 0,
          label:
            'É cuidadoso quando a questão é dinheiro, ora continuamente para a sua distribuição adequada na obra do Senhor.'
        },
        {
          id: 34,
          gifts: [6],
          answer: 0,
          label:
            'Se não encontra pessoas qualificadas para fazer a obra, mesmo assim não desanima; mas procura equipar outros para que façam a obra.'
        },
        {
          id: 35,
          gifts: [7],
          answer: 0,
          label:
            'Gosta de visitar órfãos de viúvas e de alguma forma ajudá-los nestes momentos difíceis.'
        }
      ]
    }
  },

  watch: {
    currentQuestion (value) {
      this.results = this.questions.reduce((acc, question) => {
        question.gifts.forEach(gift => {
          acc[gift] += question.answer
        })
        return acc
      }, this.results)
    }
  },

  computed: {
    progress () {
      return this.currentQuestion / 35
    },

    myGifts () {
      return this.gifts.filter(gift => {
        return (
          this.results[gift.id] === Math.max(...Object.values(this.results))
        )
      })
    },

    asdf () {
      return this.gifts.map((el, i) => ({
        label: el.label,
        value: this.results[i]
      }))
    }
  },

  methods: {
    setAnswer (value) {
      this.questions[this.currentQuestion - 1].answer = value
    },

    nextQuestion () {
      if (this.currentQuestion >= 35) {
        return
      }

      this.currentQuestion++
    },

    backQuestion () {
      if (this.currentQuestion <= 1) {
        return
      }

      this.currentQuestion--
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Jua&display=swap');

.area-questions {
  font-size: 20px;
  color: #fee9d0;
  padding: 10px;
  border-radius: 10px;
  background-color: #66987c;
}

.btn-back {
}

.btn-next {
}
</style>
