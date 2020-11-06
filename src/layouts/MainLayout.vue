<template>
  <q-layout view="hHh lpR lff">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
        <q-avatar square>
          <img src="~assets/logo.png">
        </q-avatar>
        <q-toolbar-title>
          Species Website (Development)
        </q-toolbar-title>

        <div>Version 2020</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label header class="text-grey-8">
          Navigation
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer bordered class="bg-grey-2 text-primary">
      <div class="q-pa-md">&copy; 2020 <a href="https://abmi.ca" target=_blank>Alberta Biodiversity Monitoring Institute</a><nbsp/>&mdash;<nbsp/><a href="http://creativecommons.org/licenses/by/4.0/" target=_blank>Creative Commons Attribution 4.0 International License</a></div>
    </q-footer>

  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Home',
    caption: '',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Lichens',
    caption: 'Fungi + algae things',
    icon: 'layers',
    link: '/lichens'
  },
  {
    title: 'Bryophytes',
    caption: 'Mosses, almost plants',
    icon: 'grass',
    link: '/mosses'
  },
  {
    title: 'Vascular plants',
    caption: 'Equipped with xylem and phloem',
    icon: 'local_florist',
    link: '/vplants'
  },
  {
    title: 'Soil mites',
    caption: 'Most legs ever',
    icon: 'bug_report',
    link: '/mites'
  },
  {
    title: 'Birds',
    caption: 'Your feathered friends',
    icon: 'radio_button_unchecked',
    link: '/birds'
  },
  {
    title: 'Mammals',
    caption: 'Those furry relatives',
    icon: 'pest_control_rodent',
    link: '/mammals'
  },
  {
    title: 'Habitat elements',
    caption: 'Things that trip you up',
    icon: 'eco',
    link: '/habitats'
  }
]

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
