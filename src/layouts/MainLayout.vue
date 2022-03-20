<template>
  <div class="q-pa-md">
    <q-layout
      view="hHh Lpr lff"
      container
      style="height: 95vh"
      class="shadow-2 rounded-borders"
    >
      <q-header elevated class="bg-black">
        <q-toolbar>
          <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
          <q-toolbar-title>Clinica</q-toolbar-title>
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above
        :mini="miniState"
        @mouseover="miniState = false"
        @mouseout="miniState = true"
        :width="200"
        :breakpoint="500"
        bordered
        class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <q-list padding>
            <q-item clickable v-ripple to="/newclient">
              <q-item-section avatar>
                <q-icon name="account_box" />
              </q-item-section>

              <q-item-section> Novo Paciente </q-item-section>
            </q-item>

            <q-item clickable v-ripple to="/" exact>
              <q-item-section avatar>
                <q-icon name="search" />
              </q-item-section>

              <q-item-section> Buscar Paciente </q-item-section>
            </q-item>

            <q-item active clickable v-ripple to="/agenda">
              <q-item-section avatar>
                <q-icon name="local_hospital" />
              </q-item-section>

              <q-item-section> Agenda Médica </q-item-section>
            </q-item>

            <q-item clickable v-ripple disable>
              <q-item-section avatar>
                <q-icon name="send" />
              </q-item-section>

              <q-item-section> Send </q-item-section>
            </q-item>

            <q-separator />

            <q-item clickable v-ripple disable>
              <q-item-section avatar>
                <q-icon name="drafts" />
              </q-item-section>

              <q-item-section> Drafts </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <keep-alive>
          <router-view />
        </keep-alive>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    return {
      drawer: ref(false),
      miniState: ref(true),
    };
  },
};
</script>
