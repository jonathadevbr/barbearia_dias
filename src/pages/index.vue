<template>
  <q-layout view="lHh Lpr lff">

    <q-header class="text-white q-pa-md" style="background: linear-gradient(to bottom, rgba(0, 0, 0, 0.7) 0%, rgba(0, 0, 0, 0) 100%); box-shadow: none;">
      <q-toolbar class="row justify-between items-center relative-position">
        <q-btn v-if="$q.screen.lt.md" flat dense round icon="menu" aria-label="Menu" @click="toggleDrawer" />

        <div class="text-body1 text-weight-bold">BARBEARIA DIAS</div>

        <q-tabs v-if="$q.screen.gt.sm" class="row justify-center">
          <q-route-tab v-for="link in linksList" :key="link.label" :to="link.link" :label="link.label" />
        </q-tabs>

        <div>
          <q-btn outline color="amber-7" label="AGENDAR" />
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="drawer" :breakpoint="500" bordered class="lt-md">
      <q-list>
        <EssentialLink v-for="link in linksList" :key="link.label" v-bind="link" />
      </q-list>
    </q-drawer>

    <!-- Page container sem padding superior para a imagem encostar no topo -->
    <q-page-container style="padding-top: 0 !important;">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import EssentialLink, { type EssentialLinkProps } from '@/components/EssentialLink.vue';

const drawer = ref(false);

const toggleDrawer = () => {
  drawer.value = !drawer.value;
};

const linksList: EssentialLinkProps[] = [
  { label: 'Serviços', link: '#' },
  { label: 'Barbeiro', link: '#' },
  { label: 'Visite', link: '#' },
];
</script>
