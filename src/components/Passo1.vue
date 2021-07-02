<template>
  <form novalidate class="md-layout" @submit.prevent="validate">
    <md-card class="md-layout-item md-size-50 md-small-size-100">
      <md-card-header>
        <div class="md-title">Dados Básicos</div>
      </md-card-header>
      <md-card-content>
        <md-field>
          <md-chips md-placeholder="Escolha os itens"></md-chips>
          <span class="text-danger">The first name is required</span>
        </md-field>
        <md-field>
          <label for="descricao">Descrição:</label>
          <md-input id="descricao" v-model="model.descricao" />
          <span class="text-danger" v-if="!$v.model.descricao.required"
            >Informe a descrição</span
          >
        </md-field>
        <md-field>
          <label for="objeto">Objeto:</label>
          <md-input id="objeto" v-model="model.objeto" />
          <span class="text-danger" v-if="!$v.model.objeto.required">Informe o Objeto</span>
        </md-field>
        <div class="row">
          <div class="col-6">
            <md-field>
              <label for="exercicio">Exercício:</label>
              <md-input
                id="exercicio"
                type="number"
                v-model="model.exercicio"
              />
              <span class="text-danger" v-if="!$v.model.exercicio.required">Informe o Exercício</span>
            </md-field>
          </div>
          <div class="col-6">
            <md-field>
              <label for="tipoCompra">Tipo de Compra:</label>
              <md-select id="tipoCompra" v-model="model.tipoCompra">
                <md-option value="0">Compra Global</md-option>
                <md-option value="1">Compra por Item</md-option>
              </md-select>
              <span class="md-error">The first name is required</span>
            </md-field>
          </div>
        </div>
      </md-card-content>

      <md-progress-bar md-mode="indeterminate" />

      <md-card-actions>
        <md-button
          type="button"
          class="md-primary"
          v-on:click="$emit('avancar')"
          >Avançar</md-button
        >
      </md-card-actions>
    </md-card>
  </form>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required } from "vuelidate/lib/validators";

export default {
  name: "Passo1",
  mixins: [validationMixin],
  props: {
    model: { type: Object, required: true },
  },
  validations: {
    model: {
      descricao: { required },
      objeto: { required },
      exercicio: { required },
    },
  },
  methods: {
    validate() {
      this.$v.$touch();

      if (!this.$v.$invalid) {
        console.log("é valido");
      }
    },
  },
};
</script>