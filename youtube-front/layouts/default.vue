<template>
  <v-app>
    <v-navigation-drawer
      :mini-variant="isMiniVariant"
      :mini-variant-width="60"
      :clipped="true"
      fixed
      app
    >
      <list class="px-4" :items="linksList.filter((link) => link.section === 'mainLinks')"></list>

      <v-divider v-if="!isMiniVariant"></v-divider>

      <list class="px-4" :items="linksList.filter((link) => link.section === 'personalLinks')"></list>

      <span v-if="!isMiniVariant">
        <v-divider ></v-divider>
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
          <list class="px-4" :items="linksList.filter((link) => link.section === 'genreLinks')"></list>
        </div>

        <v-divider></v-divider>
        <list class="px-4" :items="linksList.filter((link) => link.section === 'browseLinks')"></list>

        <v-divider></v-divider>
        <div class="py-3">
          <h4 class="mx-8 grey--text lighten-1">MORE FROM YOUTUBE</h4>
          <list class="px-4" :items="linksList.filter((link) => link.section === 'premiumLinks')"></list>
        </div>

        <v-divider></v-divider>
        <list class="px-4" :items="linksList.filter((link) => link.section === 'otherLinks')"></list>

        <v-divider></v-divider>
        <v-footer style="background-color: #363636">
          <div class="px-4 caption font-weight-bold">
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
      </span>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="true"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="isMiniVariant = !isMiniVariant" />
      <a
        class="text-decoration-none white--text"
        href="/"
      >
        <v-img
          class="white--text"
          width="25"
          src="https://upload.wikimedia.org/wikipedia/commons/e/e1/YouTube_play_buttom_icon_%282013-2017%29.svg"
          max-height="100px"
          max-width="300px"
        >
        </v-img>
      </a>
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
      linksList: [
        {
          section: 'mainLinks',
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          section: 'mainLinks',
          icon: 'mdi-fire',
          title: 'Trending',
          to: '/trending'
        },
        {
          section: 'mainLinks',
          icon: 'mdi-youtube-subscription',
          title: 'Subscriptions',
          to: '/subscription'
        },
        {
          section: 'personalLinks',
          icon: 'mdi-play-box-multiple',
          title: 'Library',
          to: '/library'
        },
        {
          section: 'personalLinks',
          icon: 'mdi-history',
          title: 'History',
          to: '/history'
        },
        {
          section: 'genreLinks',
          icon: 'mdi-music',
          title: 'Music',
          to: '/music'
        },
        {
          section: 'genreLinks',
          icon: 'mdi-trophy',
          title: 'Sport',
          to: '/sport'
        },
        {
          section: 'genreLinks',
          icon: 'mdi-youtube-gaming',
          title: 'Gaming',
          to: '/gaming'
        },
        {
          section: 'genreLinks',
          icon: 'mdi-newspaper',
          title: 'News',
          to: '/news'
        },
        {
          section: 'genreLinks',
          icon: 'mdi-broadcast',
          title: 'Live',
          to: '/live'
        },
        {
          section: 'genreLinks',
          icon: 'mdi-virtual-reality',
          title: '360° Video',
          to: '/virtual'
        },
        {
          section: 'browseLinks',
          icon: 'mdi-plus-circle',
          title: 'Browse channels',
          to: '/browse'
        },
        {
          section: 'premiumLinks',
          icon: 'mdi-youtube',
          title: 'YouTube Premium',
          to: '/music'
        },
        {
          section: 'premiumLinks',
          icon: 'mdi-broadcast',
          title: 'Live',
          to: '/live'
        },
        {
          section: 'otherLinks',
          icon: 'mdi-cog',
          title: 'Settings',
          to: '/settings'
        },
        {
          section: 'otherLinks',
          icon: 'mdi-flag',
          title: 'Report history',
          to: '/reports'
        },
        {
          section: 'otherLinks',
          icon: 'mdi-help-circle',
          title: 'Help',
          to: '/help'
        },
        {
          section: 'otherLinks',
          icon: 'mdi-message-alert',
          title: 'Send feedback',
          to: '/feedback'
        },
      ],
    }
  }
}
</script>

<style>
  ::-webkit-scrollbar {
    width: 8px;
  }

  ::-webkit-scrollbar-track {
    background: #363636;
  }

  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
</style>
