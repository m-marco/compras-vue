<template>
  <div>
    <md-list-item>
      <md-avatar>
        {{itemIndex}}
      </md-avatar>

      <div class="md-list-item-text">
        <div class="row">
          <div class="col-9">
            <span>{{ item.codigoItem }} - {{ item.nomeItem }}</span>
          </div>
          <div class="col-3">
            <md-field>
              <label for="quantidade">Quantidade:</label>
              <md-input
                id="quantidade"
                type="number"
                v-model="item.quantidade"
              />
              <span class="md-error">The first name is required</span>
            </md-field>
          </div>
        </div>
      </div>
      <md-button class="md-icon-button md-list-action" v-on:click="$emit('removerItemCotacao')">
        <md-icon class="md-accent">delete_forever</md-icon>
      </md-button>
    </md-list-item>
    <md-divider class="md-inset"></md-divider>
  </div>
</template>

<script>
export default {
  name: "ItemCotacao",
  emits: ['removerItemCotacao'],
  props: ["item", "itemIndex"],
};
</script>