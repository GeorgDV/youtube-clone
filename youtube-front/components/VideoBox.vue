<template>
  <v-container class="container d-inline-block">
    <div class="container__content">
      <v-row>
        <v-col class="video">
          <img
            class="video--thumbnail"
            :src="require(`../static/thumbnails/${source.id}.webp`)"
            alt="thumbnail"
          />
          <div class="video--overlay rounded px-1">
            {{ source.length }}
          </div>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col-2 video__channel--logo">
          <img
            class="rounded-circle m-auto"
            :src="require(`../static/channels/${source.channelId}.webp`)"
            alt="thumbnail"
          />
        </v-col>
        <v-col class="col-10 video__title">
          <p class="video__title--content white--text">
            {{ source.title }}
          </p>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col-2"></v-col>
        <v-col class="col-10 video__description">
          <p class="grey--text text--lighten-1 body-2">
            <v-tooltip top>
              <template v-slot:activator="{ on, attrs }">
                <a
                  class="grey--text text--lighten-1 text-decoration-none"
                  :href="'/' + source.channel"
                  v-bind="attrs"
                  v-on="on"
                >
                  {{ source.channel }}
                </a>
              </template>
              <span>{{ source.channel }}</span>
            </v-tooltip>
            <v-icon class="ml-1 grey--text lighten-1" size="0.875rem">
              mdi-check-circle
            </v-icon>
            <br />
            {{ source.views }} views • {{ source.dateAdded }}
          </p>
        </v-col>
      </v-row>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "VideoBox.vue",
  props: {
    source: {
      required: true,
      default: {},
    },
  },
  computed: {
    getImgUrl(index) {
      return "../static/", index, /\.webp$/;
    },
  },
};
</script>

<style scoped>
.container {
  margin: 0.125rem;
  padding: 1rem;
  height: auto;
  width: 40vh;
  min-width: 20vh;
  max-width: 40vh;
}

.container__content:hover {
  cursor: pointer;
}

.video {
  position: relative;
  padding: 0.25rem;
}

.video--thumbnail {
  width: 100%;
  height: 20vh;
}

.video__channel--logo {
  padding: 0.125rem 0 0 0;
}

.video__channel--logo img {
  display: block;
  margin: 0.25rem auto;
  height: 2.5rem;
  width: 2.5rem;
}

.video__title {
  padding: 0.25rem 0.5rem 0;
  height: auto;
}

.video__title--content {
  margin: 0;
}

.video__description {
  padding: 0.5rem;
  padding-top: 0;
}

.video--overlay {
  position: absolute;
  width: fit-content;
  background-color: black;
  bottom: 0.825rem;
  right: 0.5rem;
}
</style>