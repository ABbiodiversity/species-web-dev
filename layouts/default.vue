<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      clipped
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      dark
      color="#4C515A"
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-img src="/abmi-logo.png" max-height="40" max-width="40" contain alt="ABMI Logo"></v-img>
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      absolute
      app
    >
      <span>
        <small>
        &copy; {{ new Date().getFullYear() }}
        <a
          href="https://www/abmi.ca"
          target="_blank"
          rel="noopener noreferrer"
          title="ABMI Website"
        >
           Alberta Biodiversity Monitoring Institute
        </a>
        &mdash;
        <a
          href="http://creativecommons.org/licenses/by/4.0/"
          target="_blank"
          rel="noopener noreferrer"
          title="Creative Commons License"
        >
           Creative Commons Attribution 4.0 International License
        </a>
        </small>
      </span>
    </v-footer>
  </v-app>
</template>
<style>
.v-card__text, .v-card__title {
  word-break: normal; /* maybe !important  */
}
</style>
<script>
export default {
  data () {
    return {
      title: 'ABMI SC Dev',
      drawer: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-layers',
          title: 'Lichens',
          to: '/lichens/'
        },
        {
          icon: 'mdi-grass',
          title: 'Bryophytes',
          to: '/mosses/'
        },
        {
          icon: 'mdi-flower',
          title: 'Plants',
          to: '/vplants/'
        },
        {
          icon: 'mdi-bug',
          title: 'Mites',
          to: '/mites/'
        },
        {
          icon: 'mdi-bird',
          title: 'Birds',
          to: '/birds/'
        },
        {
          icon: 'mdi-cat',
          title: 'Mammals',
          to: '/mammals/'
        },
        {
          icon: 'mdi-pine-tree',
          title: 'Habitats',
          to: '/habitats/'
        },
      ]
    }
  }
}
</script>
