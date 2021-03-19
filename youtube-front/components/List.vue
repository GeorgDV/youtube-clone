<template>
  <v-list>
    <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
      <v-list-item-action>
        <v-icon class="text--secondary">{{ item.icon }}</v-icon>
        <span
          v-if="displayTitleMinimized"
          class="list-item__mini-title font-weight-light align-self-center"
        >
          {{ item.title }}
        </span>
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
    displayTitleMinimized: {
      required: false,
      default: false,
    }
  },
};
</script>

<style scoped>
.list-item__text {
  font-size: 0.875rem;
}

.list-item__mini-title {
  font-size: 0.65rem;
  margin-top: 0.25rem;
}
</style>
