<template>
  <q-page-container>
    <q-dialog>
      <q-input
        outlined
        bottom-slots
        v-model="dados.nomePaciente"
        label="Paciente"
        disable
      />

      <q-input
        outlined
        bottom-slots
        v-model="dados.cpfPaciente"
        label="CPF"
        disable
        mask="###.###.###-##"
      />
    </q-dialog>
  </q-page-container>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';

export default defineComponent({
  name: 'ClientCard',

  props: {
    client: [],
  },

  data() {
    dados: [];
  },

  setup() {
    onMounted: {
      this.loadData();
    }
  },

  methods: {
    loadData() {
      this.dados = this.client;
    },
  },
});
</script>
