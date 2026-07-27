<template>
  <q-layout view="hHh Lpr lFf">
    <q-header elevated class="bg-black text-white">
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleDrawer" class="q-mr-sm lt-md" />

        <q-toolbar-title> Barbearia Dias </q-toolbar-title>

        <div class="gt-xs">O melhor para você e seu cabelo</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="drawer" show-if-above :mini="miniState" @mouseenter="handleMouseEnter"
      @mouseleave="handleMouseLeave" :width="300" :breakpoint="500" bordered mini-to-overlay>
      <q-list>
        <EssentialLink v-for="link in linksList" :key="link.label" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import EssentialLink, { type EssentialLinkProps } from '@/components/EssentialLink.vue';

const drawer = ref(false);
const miniState = ref(true);

const toggleDrawer = () => {
  drawer.value = !drawer.value;
};

const handleMouseEnter = () => {
  if (window.innerWidth >= 500) {
    miniState.value = false;
  }
};

const handleMouseLeave = () => {
  if (window.innerWidth >= 500) {
    miniState.value = true;
  }
};

const linksList: EssentialLinkProps[] = [
  {
    label: 'Quem somos',
    icon: 'group',
    link: '#',
  },
  {
    label: 'Espaço',
    icon: 'storefront',
    link: '#',
  },
  {
    label: 'Catálogo',
    icon: 'content_cut',
    link: '#',
  },
  {
    label: 'Localização',
    icon: 'place',
    link: '#',
  },
  {
    label: 'Redes sociais',
    icon: 'share',
    link: '#',
  },
];
</script>
