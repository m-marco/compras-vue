<template>
  <div id="app" class="container">
    <div>
      <md-steppers :md-active-step.sync="passo">
        <md-step md-label="Escolha os Itens" id="passo1">
          <passo1 v-bind:model="passo1" v-on:avancar="passo = 'passo2'" />
        </md-step>
        <md-step md-label="Defina as Quantidades" id="passo2">
          <passo2
            v-bind:model="passo2"
            v-on:avancar="passo = 'passo3'"
            v-on:voltar="passo = 'passo1'"
            v-on:removerItemCotacao="removerItemCotacao"
          />
        </md-step>
        <md-step md-label="Informe os Orçamentos" id="passo3">
          <!-- <passo3 /> -->
        </md-step>
        <md-step md-label="Finalize a Cotação" id="passo4">
          <!-- <passo4 /> -->
        </md-step>
      </md-steppers>
    </div>
  </div>
</template>

<script>
import Passo1 from "./components/Passo1.vue";
import Passo2 from "./components/Passo2.vue";
// import Passo3 from "./components/Passo3.vue";
// import Passo4 from "./components/Passo4.vue";

import { validationMixin } from "vuelidate";
import { required } from "vuelidate/lib/validators";

export default {
  name: "App",
  mixins: [validationMixin],
  data() {
    return {
      passo1: {
        itensId: [],
        descricao: null,
        objeto: null,
        exercicio: 2021,
        tipoCompra: 0,
      },
      passo2: {
        itensCotacao: [
          {
            itemId: 0,
            codigoItem: "01.01",
            nomeItem: "Borracha",
            quantidade: 1,
            unidadeCompra: "Unidade",
            unidadeCompraId: 1,
          },
          {
            itemId: 1,
            codigoItem: "01.01",
            nomeItem: "Lápis",
            quantidade: 1,
            unidadeCompra: "Unidade",
            unidadeCompraId: 1,
          },
          {
            itemId: 2,
            codigoItem: "01.01",
            nomeItem: "Caneta Preta",
            quantidade: 1,
            unidadeCompra: "Unidade",
            unidadeCompraId: 1,
          },
        ],
      },
      passo: "passo1",
      itensCotacao: [],
      orcamentos: [],
    };
  },
  validations: {
    passo1: {
      descricao: required,
      objeto: required,
      exercicio: required,
    },
  },
  components: {
    Passo1,
    Passo2,
    // Passo3,
    // Passo4,
  },
  methods: {
    removerItemCotacao(itemCotacaoIndex) {
      console.log("chegou aqui");
      console.log(itemCotacaoIndex);
      this.passo2.itensCotacao.splice(itemCotacaoIndex, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
