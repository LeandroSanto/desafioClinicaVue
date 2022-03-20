<template>
  <q-page-container>
    <q-card>
      <q-input
        outlined
        bottom-slots
        v-model="text"
        label="Buscar Médico"
        placeholder="Informe o nome do médico"
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>
      <footer class="footerSearch">
        <q-btn label="Buscar" color="primary" />
      </footer>
    </q-card>

    <q-card>
      <div style="max-width: 800px; width: 100%">
        <q-calendar
          v-model="selectedDate"
          view="week"
          locale="en-us"
          style="height: 400px"
          class="col"
        />
      </div>
    </q-card>
  </q-page-container>
</template>

<script>
import { QCalendar } from '@quasar/quasar-ui-qcalendar';
export default {
  components: {
    QCalendar,
  },
  data() {
    return {
      selectedDate: '',
    };
  },
};
</script>
