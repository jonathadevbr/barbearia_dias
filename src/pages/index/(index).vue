<template>
  <q-page class="column">
    <div id="hero-section">
      <HeroSection />
    </div>

    <div id="quem-somos">
      <QuemSomos />
    </div>

    <div id="espaco-section">
      <EspacoSection />
    </div>

    <div id="catalogo-servico">
      <CatalogoServicos />
    </div>

    <div id="localizacao-contato">
      <LocalizacaoContato />
    </div>

    <div id="redes-sociais">
      <RedesSociais />
    </div>

  </q-page>
</template>

<script setup lang="ts">
import HeroSection from '../../components/HeroSection.vue'
import CatalogoServicos from '../../components/CatalogoServicos.vue'
import QuemSomos from '@/components/QuemSomos.vue';
import EspacoSection from '@/components/EspacoSection.vue';
import LocalizacaoContato from '@/components/LocalizacaoContato.vue';
import RedesSociais from '@/components/RedesSociais.vue';
</script>
