<template>
  <md-card class="md-layout-item md-size-50 md-small-size-100">
    <md-card-header>
      <div class="md-title">
        Definindo as Unidades de Compra e as Quantidades
      </div>
    </md-card-header>
    <md-card-content>
      <md-list class="md-triple-line">
        <ItemCotacao
          v-for="(item, index) in model.itensCotacao"
          v-bind:key="index"
          v-bind:itemIndex="index"
          v-bind:item="item"
          v-on:removerItemCotacao="$emit('removerItemCotacao', index)"
        />
      </md-list>
    </md-card-content>

    <md-card-actions>
      <md-button type="button" class="md-secondary" v-on:click="$emit('voltar')"
        >Voltar</md-button
      >
      <md-button type="button" class="md-primary" v-on:click="$emit('avancar')"
        >Avançar</md-button
      >
    </md-card-actions>
  </md-card>
</template>

<script>
import ItemCotacao from "./ItemCotacao.vue";

export default {
  name: "Passo2",
  emits: ['removerItemCotacao'],
  props: {
    model: { type: Object, required: true },
  },
  components: {
    ItemCotacao,
  },
};
</script>