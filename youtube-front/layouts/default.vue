<template>
  <v-app>
    <v-navigation-drawer
      value="true"
      :mini-variant="isMiniVariant"
      :clipped="true"
      fixed
      app
    >
      <list class="px-4" :items="mainItems"></list>

      <v-divider></v-divider>

      <list class="px-4" :items="secondaryItems"></list>

      <v-divider></v-divider>

      <div class="py-3 px-8">
        <p>Sign in to like videos, comment and subscribe.</p>
        <v-btn
          outlined
          color="#3ea6ff"
        >
          <v-icon class="mr-1"> mdi-account-circle </v-icon>
          Sign In
        </v-btn>
      </div>

      <v-divider></v-divider>

      <div class="py-3">
        <h4 class="mx-8 grey--text lighten-1">BEST OF YOUTUBE</h4>
        <list class="px-4" :items="genreItems"></list>
      </div>

      <v-divider></v-divider>

      <list class="px-4" :items="browseItems"></list>

      <v-divider></v-divider>

      <div class="py-3">
        <h4 class="mx-8 grey--text lighten-1">MORE FROM YOUTUBE</h4>
        <list class="px-4" :items="premiumItems"></list>
      </div>

      <v-divider></v-divider>

      <v-footer style="background-color: #363636">
        <div class="px-4">
          <p>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/about">About &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/press">Press &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/copyright">Copyright &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/contact">Contact us &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/creator">Creator &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/advertise">Advertise &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/developers">Developers</a>
          <p>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/terms">Terms &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/policyandsafety">Policy & Safety &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/howitworks">How YouTube works &nbsp;</a>
            <a class="grey--text text--lighten-1 text-decoration-none" href="/testnewfeatures">Test new features</a>
          </p>
          <p class="grey--text text--darken-1">© 2021 Google LLC</p>
        </div>
      </v-footer>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="true"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="isMiniVariant = !isMiniVariant" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-container>
        <v-row>
          <v-spacer />
          <v-textarea
            class="rounded-0"
            label="Search"
            outlined
            rows="1"
            row-height="15"
            no-resize
          ></v-textarea>
          <v-btn
            class="grey darken-3 rounded-0"
          >
            <v-icon>mdi-magnify</v-icon>
          </v-btn>
          <v-spacer />
        </v-row>
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import List from '/components/List.vue';

export default {
  components: {
    List,
  },
  data () {
    return {
      title: 'YouTube',
      isMiniVariant: false,
      mainItems: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-fire',
          title: 'Trending',
          to: '/trending'
        },
        {
          icon: 'mdi-youtube-subscription',
          title: 'Subscriptions',
          to: '/subscription'
        }
      ],
      secondaryItems: [
        {
          icon: 'mdi-play-box-multiple',
          title: 'Library',
          to: '/library'
        },
        {
          icon: 'mdi-history',
          title: 'History',
          to: '/history'
        }
      ],
      genreItems: [
        {
          icon: 'mdi-music',
          title: 'Music',
          to: '/music'
        },
        {
          icon: 'mdi-trophy',
          title: 'Sport',
          to: '/sport'
        },
        {
          icon: 'mdi-youtube-gaming',
          title: 'Gaming',
          to: '/gaming'
        },
        {
          icon: 'mdi-newspaper',
          title: 'News',
          to: '/news'
        },
        {
          icon: 'mdi-broadcast',
          title: 'Live',
          to: '/live'
        },
        {
          icon: 'mdi-virtual-reality',
          title: '360° Video',
          to: '/virtual'
        }
      ],
      browseItems: [
        {
          icon: 'mdi-plus-circle',
          title: 'Browse channels',
          to: '/browse'
        }
      ],
      premiumItems: [
        {
          icon: 'mdi-youtube',
          title: 'YouTube Premium',
          to: '/music'
        },
        {
          icon: 'mdi-broadcast',
          title: 'Live',
          to: '/live'
        }
      ],
    }
  }
}
</script>
