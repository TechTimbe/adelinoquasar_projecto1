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
          @click="toggleLeftDrawer"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
      <div class="text-h3">Agenda de Tarefas</div>
      <di class="text-subtitle1">{{ todayDate }}</di>
      </div>
      <q-img
      src="../../public/icons/imagens/montanha.jpg"
      class="header-image absolute-top"/>
      
    </q-header>
    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      :width="220"
        :breakpoint="400"
    >

        <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item 
            to="/"
            exact
            clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>
              <q-item-section>
                Tarefas
              </q-item-section>
            </q-item>
            <q-item
            to="/help"
             clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>
              <q-item-section>
                Ajuda
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
        <q-img class="absolute-top" src="../../public/icons/imagens/montanha.jpg" style="height: 192px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="../../public/icons/imagens/me.jpg">
            </q-avatar>
            <div class="text-weight-bold">Adelino Timbe</div>
            <div>@TechTimbe</div>
          </div>
        </q-img>
    </q-drawer>
    <q-page-container>
    <Keep-alive>
      <router-view />
    </Keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { computed, defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'
import { date } from 'quasar'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    // EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)
    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
}},
computed: {
        todayDate(){
          let timeStamp = Date.now()
          return date.formatDate(timeStamp, 'dddd D MMMM')
        }
  }
})
</script>

<style lang="scss">
  .header-image {
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%);
  }

</style>

