<template>
  <v-app>
    <v-navigation-drawer
      color="primary"
      :mini-variant="isMiniVariant"
      :mini-variant-width="60"
      :clipped="true"
      fixed
      app
    >
      <list
        class="px-4"
        :items="sidebarItems.filter((link) => link.section === 'mainLinks')"
      ></list>

      <v-divider v-if="!isMiniVariant"></v-divider>

      <list
        class="px-4"
        :items="sidebarItems.filter((link) => link.section === 'personalLinks')"
      ></list>

      <span v-if="!isMiniVariant">
        <v-divider></v-divider>
        <div class="py-3 px-8">
          <p>Sign in to like videos, comment and subscribe.</p>
          <v-btn outlined color="#065fd4" class="rounded-0">
            <v-icon class="mr-1"> mdi-account-circle </v-icon>
            Sign In
          </v-btn>
        </div>

        <v-divider></v-divider>
        <div class="py-3">
          <h4 class="mx-8 text--secondary lighten-1">BEST OF YOUTUBE</h4>
          <list
            class="px-4"
            :items="
              sidebarItems.filter((link) => link.section === 'genreLinks')
            "
          ></list>
        </div>

        <v-divider></v-divider>
        <list
          class="px-4"
          :items="sidebarItems.filter((link) => link.section === 'browseLinks')"
        ></list>

        <v-divider></v-divider>
        <div class="py-3">
          <h4 class="mx-8 text--secondary lighten-1">MORE FROM YOUTUBE</h4>
          <list
            class="px-4"
            :items="
              sidebarItems.filter((link) => link.section === 'premiumLinks')
            "
          ></list>
        </div>

        <v-divider></v-divider>
        <list
          class="px-4 red--text"
          :items="sidebarItems.filter((link) => link.section === 'otherLinks')"
        ></list>

        <v-divider></v-divider>
        <v-footer color="primary">
          <div class="px-4 caption font-weight-bold">
            <p>
              <a
                class="text--secondary text-decoration-none"
                href="/about"
                >About &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/press"
                >Press &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/copyright"
                >Copyright &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/contact"
                >Contact us &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/creator"
                >Creator &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/advertise"
                >Advertise &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/developers"
                >Developers</a
              >
            </p>

            <p>
              <a
                class="text--secondary text-decoration-none"
                href="/terms"
                >Terms &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/policyandsafety"
                >Policy & Safety &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/howitworks"
                >How YouTube works &nbsp;</a
              >
              <a
                class="text--secondary text-decoration-none"
                href="/testnewfeatures"
                >Test new features</a
              >
            </p>
            <p class="text--secondary">© 2021 Google LLC</p>
          </div>
        </v-footer>
      </span>
    </v-navigation-drawer>
    <v-app-bar color="primary" :clipped-left="true" fixed app>
      <div class="mobile">
        <v-app-bar-nav-icon @click.stop="isMiniVariant = !isMiniVariant" />
        <a class="text-decoration-none white--text" href="/">
          <v-img
            class="white--text"
            width="25"
            src="https://upload.wikimedia.org/wikipedia/commons/e/e1/YouTube_play_buttom_icon_%282013-2017%29.svg"
            max-height="100px"
            max-width="300px"
          >
          </v-img>
        </a>
        <v-toolbar-title class="title ml-1" v-text="title" />
        <sup class="text--secondary">EE</sup>

      </div>
      <v-spacer />
      <v-container>
        <v-row justify="center">
          <input
            class="search-bar--input rounded-0"
            :style="{ backgroundColor: isDarkTheme ? $vuetify.theme.themes.dark.secondary : $vuetify.theme.themes.light.primary,
                      borderColor: isDarkTheme ? $vuetify.theme.themes.dark.accent : $vuetify.theme.themes.light.accent}"
            type="text"
            placeholder="Search.."
          />
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                color="secondary"
                class="search-bar--button text--secondary elevation-0 rounded-0"
                :style="{borderColor: isDarkTheme ? $vuetify.theme.themes.dark.accent : $vuetify.theme.themes.light.accent + ' !important'}"
                v-bind="attrs"
                v-on="on"
              >
                <v-icon>mdi-magnify</v-icon>
              </v-btn>
            </template>
            <span>Search</span>
          </v-tooltip>
          <v-tooltip bottom>
            <template v-slot:activator="{ on, attrs }">
              <v-icon class="ml-3" v-bind="attrs" v-on="on" @click="">
                mdi-microphone
              </v-icon>
            </template>
            <span>Search with your voice</span>
          </v-tooltip>
        </v-row>
      </v-container>
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" class="text--primary menu-button mr-4" v-bind="attrs" v-on="on">
            <v-icon> mdi-dots-grid </v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item
            v-for="(item, index) in menuItems.filter((item) => item.type === 1)"
            :key="index + '-' + item.type"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action>
              <v-icon class="red--text">{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>

          <v-divider></v-divider>

          <v-list-item
            v-for="(item, index) in menuItems.filter((item) => item.type === 2)"
            :key="index + '-' + item.type"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action>
              <v-icon class="red--text">{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>

          <v-divider></v-divider>

          <v-list-item
            v-for="(item, index) in menuItems.filter((item) => item.type === 3)"
            :key="index + '-' + item.type"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action>
              <v-icon class="red--text">{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-menu :close-on-content-click="false" bottom offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" class="text--primary menu-button mr-2" v-bind="attrs" v-on="on">
            <v-icon> mdi-dots-vertical </v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item @click="switchTheme">
            <v-list-item-content class="ml-4">
              <v-icon class="mr-4 text--secondary lighten-1">
                {{ isDarkTheme ? 'mdi-brightness-4' : 'mdi-brightness-5'}}
              </v-icon>
            </v-list-item-content>
          </v-list-item>
          <v-list-group
            v-for="item in settingsItems.filter((item) => !!item.items)"
            v-model="item.active"
            :key="item.title"
            no-action
          >
            <template v-slot:activator>
              <v-list-item>
                <v-icon class="mr-4 text--secondary lighten-1">
                  {{ item.icon }}
                </v-icon>
                <v-list-item-content>
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item
              v-for="subItem in item.items"
              :key="subItem.title"
              @click=""
            >
              <v-list-item-content>
                <v-list-item-title>{{ subItem.title }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
          <v-list-item
            v-for="item in settingsItems.filter((item) => !item.items)"
            :key="item.title + '-single'"
            :to="item.to"
          >
            <v-icon class="mx-4 text--secondary"> {{ item.icon }} </v-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-divider></v-divider>

          <v-list-item @click="isRestrictedMode = !isRestrictedMode">
            <v-list-item-content class="ml-4">
              <v-list-item-title>Restricted Mode: {{ isRestrictedMode ? 'On' : 'Off'}}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn outlined color="#065fd4" class="rounded-0">
        <v-icon class="mr-1"> mdi-account-circle </v-icon>
        Sign In
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container class="container">
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import List from "/components/List.vue";

export default {
  components: {
    List,
  },
  data() {
    return {
      title: "YouTube",
      isMiniVariant: false,
      isRestrictedMode: false,
      isDarkTheme: this.$vuetify.theme.dark,
      settingsItems: [
        {
          title: "Appearance",
          icon: "mdi-brightness-4",
          items: [
            { title: "Use device theme" },
            { title: "Dark theme" },
            { title: "Light theme" },
          ],
        },
        {
          title: "Language: British English",
          icon: "mdi-translate",
          items: [
            { title: "British English" },
            { title: "American English" },
            { title: "Russian" },
            { title: "Chinese" },
            { title: "Spanish" },
            { title: "German" },
            { title: "French" },
          ],
        },
        {
          title: "Location: Estonia",
          icon: "mdi-web",
          items: [
            { title: "Estonia" },
            { title: "United States" },
            { title: "Russia" },
            { title: "China" },
            { title: "Spain" },
            { title: "Germany" },
            { title: "France" },
          ],
        },
        {
          title: "Settings",
          icon: "mdi-cog",
          to: "/settings",
        },
        {
          title: "Your data in YouTube",
          icon: "mdi-shield-account",
          to: "/yourdata",
        },
        {
          title: "Help",
          icon: "mdi-help-circle",
          to: "/help",
        },
        {
          title: "Send feedback",
          icon: "mdi-message-alert",
          to: "/feedback",
        },
        {
          title: "Keyboard shortcuts",
          icon: "mdi-keyboard",
          to: "/shortcuts",
        },
      ],
      menuItems: [
        {
          type: 1,
          icon: "mdi-youtube-tv",
          title: "YouTube TV",
          to: "/yttv",
        },
        {
          type: 2,
          icon: "mdi-play-circle",
          title: "YouTube Music",
          to: "/ytmusic",
        },
        {
          type: 2,
          icon: "mdi-youtube",
          title: "YouTube Kids",
          to: "/ytkids",
        },
        {
          type: 3,
          icon: "mdi-youtube",
          title: "Creator Academy",
          to: "/ytstudio",
        },
        {
          type: 3,
          icon: "mdi-youtube",
          title: "YouTuve for Artists",
          to: "/ytartists",
        },
      ],
      sidebarItems: [
        {
          section: "mainLinks",
          icon: "mdi-home",
          title: "Home",
          to: "/",
        },
        {
          section: "mainLinks",
          icon: "mdi-fire",
          title: "Trending",
          to: "/trending",
        },
        {
          section: "mainLinks",
          icon: "mdi-youtube-subscription",
          title: "Subscriptions",
          to: "/subscription",
        },
        {
          section: "personalLinks",
          icon: "mdi-play-box-multiple",
          title: "Library",
          to: "/library",
        },
        {
          section: "personalLinks",
          icon: "mdi-history",
          title: "History",
          to: "/history",
        },
        {
          section: "genreLinks",
          icon: "mdi-music",
          title: "Music",
          to: "/music",
        },
        {
          section: "genreLinks",
          icon: "mdi-trophy",
          title: "Sport",
          to: "/sport",
        },
        {
          section: "genreLinks",
          icon: "mdi-youtube-gaming",
          title: "Gaming",
          to: "/gaming",
        },
        {
          section: "genreLinks",
          icon: "mdi-newspaper",
          title: "News",
          to: "/news",
        },
        {
          section: "genreLinks",
          icon: "mdi-broadcast",
          title: "Live",
          to: "/live",
        },
        {
          section: "genreLinks",
          icon: "mdi-virtual-reality",
          title: "360° Video",
          to: "/virtual",
        },
        {
          section: "browseLinks",
          icon: "mdi-plus-circle",
          title: "Browse channels",
          to: "/browse",
        },
        {
          section: "premiumLinks",
          icon: "mdi-youtube",
          title: "YouTube Premium",
          to: "/music",
        },
        {
          section: "premiumLinks",
          icon: "mdi-broadcast",
          title: "Live",
          to: "/live",
        },
        {
          section: "otherLinks",
          icon: "mdi-cog",
          title: "Settings",
          to: "/settings",
        },
        {
          section: "otherLinks",
          icon: "mdi-flag",
          title: "Report history",
          to: "/reports",
        },
        {
          section: "otherLinks",
          icon: "mdi-help-circle",
          title: "Help",
          to: "/help",
        },
        {
          section: "otherLinks",
          icon: "mdi-message-alert",
          title: "Send feedback",
          to: "/feedback",
        },
      ],
    };
  },
  methods: {
    switchTheme() {
      this.isDarkTheme = !this.isDarkTheme;
      this.$vuetify.theme.dark = this.isDarkTheme;
    },
  },
};
</script>

<style>
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #8b8b8b;
}

::-webkit-scrollbar-thumb {
  background: rgb(107, 107, 107);
}

::-webkit-scrollbar-thumb:hover {
  background: #555;
}

.container {
  max-width: none;
}

.title {
  min-width: 5.75rem;
}

.search-bar--input {
  width: 40%;
  padding: 1rem;
  height: 2rem;
  background-color: #121212;
  color: white;
  border-width: 1px;
  border-style: solid;
}

.search-bar--input:focus {
  outline: #3ea6ff 1px solid;
}

.search-bar--button {
  height: auto !important;
  border-width: 1px !important;
  border-style: solid !important;
}

.menu-button {
  box-shadow: none;
  padding: 0 !important;
  min-width: 2rem !important;
}

.mobile {
  display: inline-flex;
  align-items: center;
}

@media only screen and (max-width: 600px) {
  .mobile {
    display: none;
  }
}
</style>
