<template>
    <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuro}">
        <div class="column is-one-quarter">
            <BarraLateral @aoTemaAlterado="trocarTema" />
        </div>

        <div class="column is-three-quarter conteudo">
            <Formulario @aoSalvarTarefa="salvarTarefa"/>

            <div class="lista">
                <div class="box has-text-weight-bold">
                    <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
                </div>

                <Box v-if="listaVazia">
                    Você não está muito produtivo hoje!
                </Box>
            </div>
        </div>
    </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import Tarefa from './components/Tarefa.vue'
import Itarefa from './interfaces/ITarefa'
import Box from './components/Box.vue'

export default defineComponent({
  name: 'App',
  components: {
      BarraLateral,
      Formulario,
      Tarefa,
      Box
  },

  computed: {
      listaVazia() : boolean {
          return this.tarefas.length === 0
      }
  },

  data () {
      return {
          tarefas: [] as Itarefa[],
          modoEscuro: false
      }
  },

  methods: {
      salvarTarefa (tarefa: Itarefa) {
          this.tarefas.push(tarefa)
      },

      trocarTema (modoEscuro: boolean) {
          this.modoEscuro = modoEscuro
      }
  }
  
});
</script>

<style>
.lista {
    padding: 1.25rem;
}

main {
    --bg-primeirio: #FFFFFF;
    --texto-primario: #000000;
}

main.modo-escuro {
    --bg-primeirio: #2B2D42;
    --texto-primario: #DDDDDD;
}

.conteudo {
    background-color: var(--bg-primeirio);
}
</style>