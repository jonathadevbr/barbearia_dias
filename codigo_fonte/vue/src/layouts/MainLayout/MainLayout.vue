<template>
    <q-layout view="hHh LpR lFf">
        <!--Cabeçalho-->
        <q-header class="row items-center" :class="$q.dark.isActive ? 'header_dark' : 'header_normal'">
            <!--Botão sidebar-->
            <!-- adicionar drawer para side bar encolher e expandir0@click="drawer = !drawer" -->
            <q-btn flat class="q-py-md" @click="drawer = !drawer" :style="{ borderRadius: '0px' }">
                <q-icon name="menu" />
            </q-btn>

            <!--Titulo cabeçalho-->
            <q-toolbar-title>
                <q-btn flat class="q-py-md" :style="{ borderRadius: '0px' }">
                    <h1 style="font-size: 1.1rem; line-height: 0rem; letter-spacing: 0.155rem">
                        <strong>Barbearia Dias</strong>
                    </h1>
                </q-btn>
            </q-toolbar-title>

            <!--Botões do usuario-->
            <q-btn-group flat class="items-baseline" :style="{ borderRadius: '0px! important' }">
                <!--Modo escuro-->
                <q-btn v-show="true" flat @click="$q.dark.toggle()">
                    <q-tooltip> {{ $q.dark.isActive ? 'Mode escuro' : 'Modo claro' }} ativado! </q-tooltip>
                    <q-icon :name="$q.dark.isActive ? 'nights_stay' : 'wb_sunny'" />
                </q-btn>
            </q-btn-group>
        </q-header>

        <!--Side-->
        <q-drawer v-model="drawer" show-if-above :mini="miniState" @mouseenter="miniState = false"
            @mouseleave="miniState = true" mini-to-overlay :width="300" :breakpoint="500" bordered
            :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'">
            <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
                <q-list padding>
                    <q-item clickable v-ripple to="/" exact>
                        <q-item-section avatar>
                            <q-icon name="person" />
                        </q-item-section>

                        <q-item-section>
                            SOBRE NÓS
                        </q-item-section>
                    </q-item>

                    <q-item clickable v-ripple to="/localizacao">
                        <q-item-section avatar>
                            <q-icon name="location_pin" />
                        </q-item-section>

                        <q-item-section>
                            LOCALIZAÇÃO
                        </q-item-section>
                    </q-item>

                    <q-item clickable v-ripple to="/agende">
                        <q-item-section avatar>
                            <q-icon name="watch_later" />
                        </q-item-section>

                        <q-item-section>
                            AGENDE SEU HORÁRIO
                        </q-item-section>
                    </q-item>

                    <q-item clickable v-ripple to="/catalogo">
                        <q-item-section avatar>
                            <q-icon name="content_cut" />
                        </q-item-section>

                        <q-item-section>
                            CATÁLOGO
                        </q-item-section>
                    </q-item>
                </q-list>
            </q-scroll-area>
        </q-drawer>

        <q-page-container>
            <router-view />
        </q-page-container>

    </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
    setup() {
        return {
            drawer: ref(false),
            miniState: ref(true)
        }
    }
}</script>