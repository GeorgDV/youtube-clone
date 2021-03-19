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
          <div class="video--overlay white--text rounded px-1">
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
          <p class="video__title--content text--primary font-weight-bold">
            {{ source.title }}
          </p>
        </v-col>
      </v-row>
      <v-row>
        <v-col class="col-2"></v-col>
        <v-col class="col-10 video__description">
          <p class="video__description--content text--secondary text--lighten-1 body-2">
            <v-tooltip top>
              <template v-slot:activator="{ on, attrs }">
                <a
                  class="text--secondary font-weight-medium text-decoration-none"
                  :href="'/' + source.channelName"
                  v-bind="attrs"
                  v-on="on"
                >
                  {{ source.channelName }}
                  <v-icon class="ml-1 text--secondary font-weight-medium lighten-1" size="0.875rem">
                    mdi-check-circle
                  </v-icon>
                </a>
              </template>
              <span class="white--text font-weight-medium">{{ source.channelName }}</span>
            </v-tooltip>
            <br />
            <span class="text--secondary font-weight-medium">
              {{ source.views }} views • {{ source.dateAdded }}
            </span>
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
  max-width: 24rem;
  max-height: 22rem;
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
  height: auto;
}

.video__channel--logo {
  padding: 0.125rem 0 0 0;
}

.video__channel--logo img {
  display: block;
  margin: 0.25rem auto;
  height: 2.25rem;
  width: 2.25rem;
}

.video__title {
  padding: 0.25rem 0.5rem 0;
  height: auto;
}

.video__title--content {
  margin: 0;
  overflow: hidden;
  text-overflow: ellipsis;
}

.video__description {
  padding: 0.5rem;
  padding-top: 0;
}

.video__description--content {
  overflow: hidden;
  text-overflow: ellipsis;
}

.video--overlay {
  position: absolute;
  width: fit-content;
  background-color: black;
  bottom: 0.825rem;
  right: 0.5rem;
}
</style>