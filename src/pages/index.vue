<template>
  <q-layout view="lHh Lpr lFf">
    <!-- Cabeçalho em preto e branco -->
    <q-header elevated class="bg-black text-white">
      <q-toolbar>

        <q-toolbar-title> Barbearia Dias </q-toolbar-title>

        <div>O melhor para você e seu cabelo</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="drawer" show-if-above :mini="miniState" @mouseenter="miniState = false"
      @mouseleave="miniState = true" :width="300" :breakpoint="500" bordered>
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

const drawer = ref(false)
const miniState = ref(true)

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
