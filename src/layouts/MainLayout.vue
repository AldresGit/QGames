<template>
  <q-layout view="lHh Lpr lFf">
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

        <q-toolbar-title>
          QProject
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Essential Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container class="q-pa-md">
      <div class="row">
        <div class="col-0 col-sm-0 col-md-1 col-lg-1"></div>
        <div class="col-12 col-sm-12 col-md-10 col-lg-10">
          <router-view />
        </div>
        <div class="col-0 col-sm-0 col-md-1 col-lg-1"></div>
      </div>
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Home',
    caption: 'Home Page',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Information',
    caption: 'Information Page',
    icon: 'info',
    link: '/#/info'
  },
  {
    title: 'Contacto',
    caption: 'La pagina de contacto',
    icon: 'contact_support',
    link: '/#/info/contact'
  },
  {
    title: 'Juegos',
    caption: 'Listado de juegos',
    icon: 'games',
    link: '/#/games'
  },
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
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
