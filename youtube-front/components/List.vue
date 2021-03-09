<template>
  <v-list>
    <v-list-item
      v-for="(item, i) in items"
      :key="i"
      :to="item.to"
      router
      exact
    >
      <v-list-item-action>
        <v-icon class="grey--text">{{ item.icon }}</v-icon>
      </v-list-item-action>
      <v-list-item-content>
        <v-list-item-title class="list-item__text" v-text="item.title" />
      </v-list-item-content>
    </v-list-item>
  </v-list>
</template>

<script>
export default {
name: "List.vue",
  props: {
    items: {
      required: true,
      default: [],
    },
  },
}
</script>

<style scoped>
  .list-item__text {
    font-size: 0.875rem;
  }
</style>
