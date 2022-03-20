<template>
  <q-page-container>
    <q-input label="Nome:" placeholder="Nome completo" />

    <q-input label="CPF:" placeholder="CPF do titular" />

    <q-input label="Clinica:" placeholder="informe a clinica esccolhida" />

    <q-input label="Convênio:" placeholder="Convênio do paciente" />

    <q-input label="Especialidade:" placeholder="Especialidade requerida" />

    <q-input label="Médico Escolhido:" placeholder="Nome completo" />

    <div class="q-gutter-sm">
      <q-item-label label="Tipo de Atendimento" />
      <q-radio v-model="shape" val="1" label="Consulta" />
      <q-radio v-model="shape" val="2" label="Revisão" />
      <q-radio v-model="shape" val="3" label="Exame" />
      <q-radio v-model="shape" val="4" label="Procedimento" />
    </div>

    <q-input outlined bottom-slots v-model="text" label="Dia" />
    <q-input outlined bottom-slots v-model="text" label="Hora" />

    <footer class="footerSave">
      <q-btn label="Salvar" color="primary" />
    </footer>
  </q-page-container>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    return {
      model: ref('2019-02-22 21:02'),
    };
  },
};
</script>
